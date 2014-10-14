BSTfile
=======

bst algorithm

<html>
<head>
<h1>Balanced Binary Search Tree</h1>
<p>
<table id="demo" style="width:100%">
</table>
</p>
<script src="http://ajax.googleapis.com/ajax/libs/jquery/1.11.1/jquery.min.js"></script>

<script type = "text/javascript"> 


var  arr =[]
var enteredString = "Entered values are ";

function InsertNumbers(elements)
{
    var numbers = /^[-+]?[0-9]+$/;  
      if(elements.match(numbers))  
      { 
		arr.push(parseInt(elements));
		enteredString= enteredString+elements+" ";
		element = document.getElementById("enteredValueLabel");
		element.innerHTML=enteredString;	  
      return true;  
      }  
      else  
      {  
      alert('Please input numbers');  
      return false;  
	}
}

window.onload = (function(){
$("#Tree").click(function(){
var n = arr.length;

var tree_jumper = (n+1)/2;
var temp;
var text = "";

var displayed = Array();
for (j = 0; j < n; j++) {
	console.log(arr[j]);
	displayed.push(false);
}
var number_of_rows = parseInt((Math.log(n+1)/Math.LN2)); 

for (i = 0; i <number_of_rows; i++) 
{
	//Start a row...
	
	text+= "<tr>";
	temp=parseInt(tree_jumper);
	console.log(i+ " tree jumper: " + temp);
	for (j = 0; j < n; j++) 
	{
		//var row; for (jj = 0; jj < n; jj++) row += displayed[jj] + " "; console.log(row);
						
		if(j==temp-1){
			  if(displayed[j] == false){
				   console.log("adding " + j);
				   //Add data to the row
				   text += "<td>"+ arr[j] +"</td>";
				   displayed[j] = true;
			   }
			   else text+="<td> </td>";
			   temp += parseInt(tree_jumper);
		}
		else{
			console.log(j + " * " +(temp-1)+" * "+ displayed[j]); 
			text+="<td> </td>";
		}
		
	}
	//End table row
	text+="</tr>";
	tree_jumper = tree_jumper/2;
}
document.getElementById("demo").innerHTML = text;
}); });


</script>
</head>
<body>

 
<label id="EnterElement">Enter the Values for Tree: </label>
<input id="enteredValue" type="text" name="ValueOfElements">
<input id="insertEle" type="button" value="Add" onclick="InsertNumbers(enteredValue.value);"/>


<p>
<label id="enteredValueLabel"></label>
</p>

<p>
<input type="button" id="Tree" value="Display Balanced BST"  />
</p>
  
<div  id="OutDiv" > 
</div>
</body>
</html>

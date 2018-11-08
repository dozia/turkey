<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
    <head>
        <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
        <title>Insert title here</title>
    </head>
  <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css">
  <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
  <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/js/bootstrap.min.js"></script>
	<body>
		
		

		<div class="container-fluid">
			<div class="row">
				<div class="col-sm-6" >
		 <form method="get">
            <table>
                <tr>
                    <td><input type="button" value="submit" id="submit"> </td>
					<td><input type="button" value="submit2" id="submit2"> </td>
                    <div id="dvTable"></div>
                </tr>
            </table>
        </form>
		</div>

	  </div>
	</div>
	</div>
    <script type="text/javascript">
  $(document).ready(function(){
    $('#submit2').click(function(){
       alert('hi!');
    });
  });
				
	var data;
        $(document).ready(function(){
            var val = "";
            $("#submit").click(function(event){
                event.preventDefault();

                $.ajax({
                    type: "GET",
                    dataType:"json",
                    url:  "https://jsonplaceholder.typicode.com/todos",
                    success: function(data) {
debugger;  
				//Create a HTML Table element.
				var table = document.createElement("TABLE");
				table.border = "1";
				table.setAttribute('class', 'table table-bordered');
			 
				//Get the count of columns.
				var columnCount = 3;
			 
				//Add the header row.
				var row = table.insertRow(-1);
				for (var i = 0; i < columnCount; i++) {
					var headerCell = document.createElement("TH");
					headerCell.innerHTML = 'Header1';
					row.appendChild(headerCell);
				}
			 
				//Add the data rows.
				for (var i = 1; i < data.length-195; i++) {
					row = table.insertRow(-1);
					for (var j = 0; j < 3; j++) {
						var cell = row.insertCell(-1);
						if (j==0) {
						cell.innerHTML = data[i].userId}
						if (j==1) {
						cell.innerHTML = data[i].id}
						if (j==2) {
						cell.innerHTML = data[i].title}
						if (j==3) {
						cell.innerHTML = data[i].completed}
					}
				}
		 
			var dvTable = document.getElementById("dvTable");
			dvTable.innerHTML = "";
			dvTable.appendChild(table);
					
                    },
                    error: function(jqXHR, textStatus, errorThrown) {
                        console.log(' Error in processing! '+textStatus);
                    }
                });
            });	
			
        });
		
		

    </script>
</html>

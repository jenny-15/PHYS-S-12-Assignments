---
layout: default
title:  "Final Project Plans"
permalink: /12/
---

### Final Project Plans
			
<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1">
<style>
body {font-family: Arial;} 

/* Style the tab */
.tab {
  overflow: hidden;
  border: 1px solid #ccc;
  background-color: #f1f1f1;
}

/* Style the buttons inside the tab */
.tab button {
  background-color: inherit;
  float: left;
  border: none;
  outline: none;
  cursor: pointer;
  padding: 14px 16px;
  transition: 0.3s;
  font-size: 17px;
}

/* Change background color of buttons on hover */
.tab button:hover {
  background-color: #ddd;
}

/* Create an active/current tablink class */
.tab button.active {
  background-color: #ccc;
}

/* Style the tab content */
.tabcontent {
  display: none;
  padding: 6px 12px;
  border: 1px solid #ccc;
  border-top: none;
}
</style>
</head>
<body>

<h2>Tabs</h2>
<p> This page contains the plans that I made throughout the project. These tabs work best in safari. If you are in chrome and the tab contents are not showing up, please click on the links. Click on the buttons inside the tabbed menu:</p>


<div class="tab">
  <button class="tablinks" onclick="openCity(event, 'Final Project Original Plan')">Final Project Original Plan</button>
  <button class="tablinks" onclick="openCity(event, 'Final Project Plan 2')">Final Project Plan 2</button>
	<button class="tablinks" onclick="openCity(event, 'Plan 3')">Final Plan</button>
</div>


<div id="Final Project Original Plan" class="tabcontent">
  <h3>Final Project Original Plan</h3>
  <p> <a href="https://docs.google.com/document/d/1lwFWprxDkQgblWIpog1j_dIiaDs_jzjJ_5lyDi-J3wg/edit?usp=sharing
">Original Plan Link</a>
	  <iframe src="https://docs.google.com/document/d/1lwFWprxDkQgblWIpog1j_dIiaDs_jzjJ_5lyDi-J3wg/edit?usp=sharing" style="width:600px; height:500px;" frameborder="0"></iframe>

</p>
</div>

<div id="Final Project Plan 2" class="tabcontent">
  <h3>Final Project Plan 2</h3>
  <p> 
	 <a href="https://docs.google.com/document/d/1g7VfImK2Aelp6CDwWc0NSYQ_VkU76Y93SXhcfRu0560
">Plan 2 Link</a>
	  
<iframe src="https://docs.google.com/document/d/1g7VfImK2Aelp6CDwWc0NSYQ_VkU76Y93SXhcfRu0560" style="width:600px; height:500px;" frameborder="0"></iframe>

 </p> 
</div>

<div id="Plan 3" class="tabcontent">
  <h3>Plan 3</h3>
	
  <p> <a href="https://docs.google.com/document/d/1iUxP3WUQkKK1ayuvKkRupLUH8T-d88zNqGBm1yYudVE/edit?usp=sharing
">Final Plan Link</a>
	<iframe src="https://docs.google.com/document/d/1iUxP3WUQkKK1ayuvKkRupLUH8T-d88zNqGBm1yYudVE/edit?usp=sharing" frameborder="0"></iframe> </p>
</div>


<script>
function openCity(evt, cityName) {
  var i, tabcontent, tablinks;
  tabcontent = document.getElementsByClassName("tabcontent");
  for (i = 0; i < tabcontent.length; i++) {
    tabcontent[i].style.display = "none";
  }
  tablinks = document.getElementsByClassName("tablinks");
  for (i = 0; i < tablinks.length; i++) {
    tablinks[i].className = tablinks[i].className.replace(" active", "");
  }
  document.getElementById(cityName).style.display = "block";
  evt.currentTarget.className += " active";
}
</script>
   
</body>
</html> 

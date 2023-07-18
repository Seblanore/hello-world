<template>
  <div>
    <h2>Vue.js and D3 Line Chart</h2>
    <svg></svg>
  </div>
</template>
<script>
import * as d3 from "d3";
export default {
    mounted() {

    const width = 1000;
    const height = 1000;

    var spaceCircles = [
        {
            "name": "Categorie 1",
            "color": "red"
        },
        {
            "name": "Categorie 2",
            "color": "blue"
        },
        {
            "name": "Categorie 3",
            "color": "yellow"
        },
        {
            "name": "Categorie 3",
            "color": "yellow"
        },
        {
            "name": "Categorie 3",
            "color": "yellow"
        },
        {
            "name": "Categorie 3",
            "color": "yellow"
        },
        {
            "name": "Categorie 3",
            "color": "yellow"
        },
        {
            "name": "Categorie 3",
            "color": "yellow"
        } 
      ];

    var svgContainer = d3.select("body").append("svg")
      .attr("width", width)
      .attr("height", height);   

    var circles = svgContainer.selectAll("circle")
      .data(spaceCircles)
      .enter()
      .append("circle");     
          
    circles
      .attr("cx", function (d, i) { return width/2 + Math.sin(360/spaceCircles.length*i* (Math.PI / 180))*100; })
      .attr("cy", function (d, i) { return height/2 - Math.cos(360/spaceCircles.length*i* (Math.PI / 180))*100; })
      .attr("r", 20 )
      .attr('stroke', 'black')
      .style("fill", function(d) {
                return d.color;
              });

      // level 1
      svgContainer.append("circle")
      .attr("cx",width/2)
      .attr("cy",height/2)
      .attr("r", 100)
      .attr('stroke', 'black')
      .style("fill", "white");

      // level 2
      svgContainer.append("circle")
      .attr("cx",width/2)
      .attr("cy",height/2)
      .attr("r", 220)
      .attr('stroke', 'black')
      .style("fill", "transparent");

      // Center point
      svgContainer.append("circle")
      .attr("cx",width/2)
      .attr("cy",height/2)
      .attr("r", 2)
      .style("fill", "black");

      var lines = svgContainer.selectAll("line")
      .data(spaceCircles)
      .enter()
      .append("line"); 

      lines
      .style("stroke", "black")
      .style("stroke-width", 1)
      .attr("x1", width/2)
      .attr("y1", height/2)
      .attr("x2", function (d, i) { return width/2 + Math.sin(360/spaceCircles.length*i* (Math.PI / 180))*220; })
      .attr("y2", function (d, i) { return height/2 - Math.cos(360/spaceCircles.length*i* (Math.PI / 180))*220; });

      circles.raise();
  },
};
</script>
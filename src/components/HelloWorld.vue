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
            "color": "red",
            "angle": 0
        },
        {
            "name": "Categorie 2",
            "color": "blue",
            "angle": 30
        },
        {
            "name": "Categorie 3",
            "color": "yellow",
            "angle": 60
        },
        {
            "name": "Categorie 3",
            "color": "yellow",
            "angle": 90
        },
        {
            "name": "Categorie 3",
            "color": "yellow",
            "angle": 120
        },
        {
            "name": "Categorie 3",
            "color": "yellow",
            "angle": 150
        },
        {
            "name": "Categorie 3",
            "color": "yellow",
            "angle": 180
        },
        {
            "name": "Categorie 3",
            "color": "yellow",
            "angle": 210
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
      .attr("cx", function (d) { return width/2 + Math.sin(d.angle)*100; })
      .attr("cy", function (d) { return height/2 + Math.cos(d.angle)*100; })
      .attr("r", 20 )
      .style("fill", function(d) {
                return d.color;
              });

      svgContainer.append("circle")
      .attr("cx",width/2)
      .attr("cy",height/2)
      .attr("r", 100)
      .style("fill", "red");

      svgContainer.append("circle")
      .attr("cx",width/2)
      .attr("cy",height/2)
      .attr("r", 2)
      .style("fill", "black");
  },
};
</script>
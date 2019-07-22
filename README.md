# Scatterplot-Graph

*Simple scatterplot graph with D3*

This is an app that allows you to create a svg scatterplot graph with d3.


...

**Home Page**

<img src="/ScatterplotGraph.PNG" title="home page" alt="home page" width="500px">



---


## Table of Contents 

> Sections
- [Sample Code](#Sample_Code)
- [Installation](#installation)
- [Features](#features)
- [Contributing](#contributing)
- [Team](#team)
- [FAQ](#faq)
- [Support](#support)
- [License](#license)


---

## Sample Code

```javascript
// sample code
    const h= 400;
    const w= 800;
    const p= 50;
    
    const svg= d3.select('body')
                 .append('svg')
                 .attr("height",h)
                 .attr("width",w);
    
    var timeArr=[];
    var dateArr=[];
    var dopeArr=[];
    var doping=[];
    var allegations=[["No doping allegations", "#ff9933"],["Riders with doping allegations","#33CCFF"]]
  //alert(json[0]["Time"].time) 
    //alert(json.length)
    for(var i=0;i<json.length;i++){
      dateArr.push(json[i]['Year']);
      json[i]['Time']=json[i]['Time'].toString().replace(':','.')
      timeArr.push(json[i]['Time']);
      if (json[i]['Doping']==""){dopeArr.push("#ff9933"); doping.push(" ")}
      if (json[i]['Doping']!=""){dopeArr.push("#33CCFF"); doping.push(json[i]['Doping'])}
    }
      var secondsArr = [];
    json.forEach(function(par) {
      var da = new Date();
      
      da.setMinutes(par.Seconds / 60);
      da.setSeconds(par.Seconds % 60);
      secondsArr.push(da);
    }); 
    
    var timeMin = d3.min(secondsArr, (d) => d);
    var timeMax = d3.max(secondsArr, (d) => d);
    var dateMin = d3.min(dateArr, (d) => d);
    var dateMax = d3.max(dateArr, (d) => d);    
    
    const yScale= d3.scaleLinear()
                    .domain([timeMin,timeMax])
                    .range([30,h-30]);
    
    const xScale= d3.scaleLinear()
                    .domain([dateMin-1,dateMax+1])
                    .range([40,w-40]);
    
    const tooltip= d3.select('body')
                   .append('div')
                   .attr('class','tooltip')
                   .attr('id','tooltip')
                   .style('opacity',0);
    
    svg.selectAll('circle')
       .data(json)
       .enter()
       .append('circle')
       .attr("cx", (d,i)=>xScale(d.Year))
       .attr("cy", (d,i)=>yScale(secondsArr[i]))
       .attr("r",5)
       .attr("data-xvalue", (d,i)=>d.Year)
       .attr("data-yvalue", (d,i)=>secondsArr[i])
       .attr("fill", (f,i)=>dopeArr[i])
       .style("stroke","grey")
       .attr("class", "dot")
       .on("mouseover", function(f,i) {
           tooltip.transition()
                  .duration(200)
                  .style("opacity", 0.9);
           tooltip.html("<b>"+f["Name"] + ":</b> " + f["Nationality"]+ "<br />"+ "<b>Year:</b> " + f["Year"] + "<br />"+"<b>Time:</b> " + f["Time"] +"<br />"+doping[i])
                  .style("left", d3.event.pageX + 10 + "px")
                  .style("top", d3.event.pageY + 10 + "px");
           tooltip.attr("data-year", f["Year"]);
            })
       .on("mouseout", function() {
           tooltip.transition()
                  .style("opacity", 0);
                   });
    
/*       .append('title')
       .text((f,i)=>f["Name"] + ": " + f["Nationality"]+ " "+ "Year: " + f["Year"] + " "+"Time: " + f["Time"] +" "+doping[i]);*/
      // .attr("height", )
      // .attr("width", )
    //alert(json[0].Time)
    const timeFormatX= d3.timeFormat("%Y");
    const timeFormatY= d3.timeFormat("%M:%S");
    const xAxis= d3.axisBottom(xScale).tickFormat(d3.format(".0f"));
    const yAxis= d3.axisLeft(yScale).tickFormat(timeFormatY);
    
    const legend=svg.selectAll('.legend')
      .data(allegations)
      .enter()
      .append("g")
      .attr("id","legend") 
      .attr("transform", "translate(600,120)")
      .style("font-size","12px");
    
    legend.append('rect')
      .attr('width', 15) 
      .attr('height', 15)
      .attr("x", 0)
      .attr("y", (f,i)=>i*25)
      .style('fill', (f,i)=>f[1])
      .style('stroke', "gray");  
    
    legend.append('text')
      .attr("x", 20)
      .attr("y", (f,i)=>i*25+10)
      .text(d=>d[0]);
    
    
    svg.append("g")
       .attr("transform","translate(" + 0 + "," + 370 + ")")
       .attr("id", "x-axis")
       .call(xAxis);
    
    svg.append("g")
       .attr("transform","translate("+55+","+0+")")
       .attr("id", "y-axis")
       .call(yAxis);
    
 svg.append("text")
    .attr("class", "y label")
    .attr("text-anchor", "end")
    .attr("y", 10)
    .attr("x",-40)
    .attr("transform", "rotate(-90)")
   .text("Time in Minutes");

```

---

## Installation
## Features
## Usage (Optional)
## Documentation (Optional)
## Tests (Optional)
## Contributing
## Team

> Contributors/People

| [**seansangh**](https://github.com/seansangh) |
| :---: |
| [![seansangh](https://avatars0.githubusercontent.com/u/45724640?v=3&s=200)](https://github.com/seansangh)    |
| [`github.com/seansangh`](https://github.com/seansangh) | 

-  GitHub user profile

---

## FAQ

- **Have any *specific* questions?**
    - Use the information provided under *Support* for answers

---

## Support

Reach out to me at one of the following places!

- Twitter at [`@wwinvestingllc`](https://twitter.com/wwinvestingllc?lang=en)
- Github at [`seansangh`](https://github.com/seansangh)

---

## Donations (Optional)

- If you appreciate the code provided herein, feel free to donate to the author via [Paypal](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=4VED5H2K8Z4TU&source=url).

[<img src="https://www.paypalobjects.com/webstatic/en_US/i/buttons/cc-badges-ppppcmcvdam.png" alt="Pay with PayPal, PayPal Credit or any major credit card" />](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=4VED5H2K8Z4TU&source=url)

---

## License

[![License](http://img.shields.io/:license-mit-blue.svg?style=flat-square)](http://badges.mit-license.org)

- **[MIT license](http://opensource.org/licenses/mit-license.php)**
- Copyright 2019 © <a>S.S.</a>

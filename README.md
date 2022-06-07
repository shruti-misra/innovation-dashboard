# Deployment Link

Our project is deployed here: https://cse512-22sp.pages.cs.washington.edu/Metro-Innovation/

# Design Decisions and Development Process

## Design Decisions

The goal of our visualization was to create a series of dashboards that helped visualize innovation activity in different U.S cities. 

### Data Rationale

Since this project was based on Shruti's research project, she had already narrowed down cities of interest to 37 out of 384 metropolitan cities in the U.S (see: https://cse512-22sp.pages.cs.washington.edu/Metro-Innovation/#background). We then started by choosing our data of interest for this project. Shruti already had federal R&D funding, venture capital funding and Small Business Innovation Research (SBIR) funding data for the 37 metropolitan areas we studied for the year 2019. We decided to normalize each type of funding by population (per capita) to account for the fact that bigger cities are likely to receive more funding because they have more people. 

Shruti also had data on the different industry sectors and technology verticals funded by venture capital in the year 2019 for each of the 37 areas. Other data, displayed on the data ban had also been collected prior to the project. Additional data was collected for universities (latitude, longitude and disciplinary breakdown) and the number of new businesses/establishments in the cities by industry sectors. We decided to focus on a single year (2019) instead of looking at temporal data because we wanted to provide a snapshot of what is going on in different cities in that specific year. More recent data from 2020 and 2021 was not considered because it is possible that the COVID-19 pandemic may have disrupted funding patterns temporarily and would not have been an accurate depiction of innovation activity. 

### Design Rationale

- A heat map is used as a filter on the cities for the data ban. We want to show the relative value of funding per capita for each city. That is, we had two nominal categories (funding types and cities) and three quantitative measures (federal R&D funding per capita, SBIR funding per capita and venture capital funding per capita)  Initially we tried bar charts, but it loses information because the three funding’s values have different scales. Then we chose a heat map, but again some information was missing because we could not apply the same color hue to three scales. So we ended up encoding the ranking by colors and showing the number in tooltip and databan. Ranking not only gives users the ability to compare the same type of funding between different cities, but also gives users the ability to compare different fundings for the same city. 

- The data ban is created to show the quick relevant stats for the city selected in heat map. Number of investors, number of new firms, and the per capita value for each type of funding are essential to answer our research question. We think that rather than using tooltips on the heat map to show the data, we want the numbers to stand out. So we increased the text font, we bold that text, and we chose graphical logos to attract attention. 

- Navigation is used because the dashboard space is not enough. We have too much information and charts to show, but the dashboard can only contain a small amount of containers if we want each chart to be visible, effective and less cluttered (less chart junk!). So in the end, the navigation function is chosen to hide and show different charts.  

- We designed three sub-dashboards that displayed information relevant to each research question so that the user could delve deeper into each topic. 

- Federal R&D funding is often dependent on the universities in or close to (<= 100 miles of the city). We were able to find funding information for each major university in different cities and their breakdown by discipline on NSF's website. We use a U.S map to plot the location of each city and color code them by city (so that users can see the number of universities near each city). The map also acts as a filter for funding information for each university broken down by STEM disciplines, which is visualized by pie charts below the map. This was our way of presenting details on demand when needed. For the pie charts, we also added a static pie chart showing the disciplinary breakdown of R&D funding totaled across all U.S universities to provide a reference for the user to compare against. 

- We used pie charts, (a static one with totals for all of the U.S for reference and a dynamic one based on the filtered city) to convey the venture capital breakdown by industry and technology vertical. Pie charts were used because we wanted to convey "parts of whole" relationships that characterize the structure of an industry sector/technology vertical in a city. And also because we had too many sectors/verticals to put on a stacked bar chart.

- Industry structure data is further categorized into employment data and new establishments data by sector. We used stacked bar charts to show a breakdown of total employment/new establishments by sector. Users can select a city from the bar chart to see a percentage breakdown of employments/establishments in each city as a way to provide "details-on-demand". 

- Finally we provided users with brief instructions to navigate the visualizations so that it is clear to them what information they can view. 

## Development Process

We used a "double diamond" approach to design (https://en.wikipedia.org/wiki/Double_Diamond_(design_process_model)). We first solified our key questions by spending time talking about what the key questions were and then converging on them as a group and deciding what more data was needed.


- Mai collected university R&D funding data broken down by disciplines and filtered by cities that were relevant to the project (~ 3 hours)
- Shruti collected university location information, employment and establishment data (~ 3 hours)
- Boyuan put brokedown employment and establishment data by sector (~2 hours)
- Boyuan, Mai, Neha and Shruti spent time data wrangling, formatting and reformatting depending on the visualization (~3 hours)

 We then developed and rapidly prototypes multiple design alternatives and ideas using various tools to see what stuck

 - Boyuan prototyped designs in Tableau (~6 hours), his prototype ended up being used a foundation for the final design
 - Neha prototyped designs in Tableau (~6 hours, link: https://public.tableau.com/app/profile/neha4029/viz/Dashboard_innovation/Dashboard_innovation). Given below is Neha's explanations of her design choices:
    - Map design (cities with highest R&D Funding): My first choice was to use a map to see which cities received the most funding. As I believed that visualizing those cities on a map would make it easier for users to understand, I used the tooltip feature to show users the funding distributed by industry in percentage format, as well as the capital invested for 2019 year.
    - Grant received by Technology: Our data contained information on how funding is distributed by industry for all cities. Instead of looking at this for each city, I wanted the user to see the overall picture of funding distribution across US cities. As is clear, healthcare receives close to half of all funding.
    - SBIR and Federal bar chart: Both types of funding are illustrated using a bar chart with the funding amount on the y axis and the city name on the x axis. I wanted the user to be able to see which cities received the most and least funding right away, which is why I used a sorted bar chart.
Cities with most funding vs employments: I wanted the user to see if there was any correlation between the cities that received funding and the employment rate. Therefore, I thought a vertical bar chart would be the best way to show the trend. This chart reduces the amount of space at the bottom of a dashboard. I tried several times to change the width of the dashboard, but it didn't work. In the future, I will do more research to determine how to set the dashboard width to fit the design.

- Shruti prototyped her design in Altair (~ 6 hours)

- Using her prototype Shruti then designed and conducted a quick survey to identify potential users and use cases (see results here: https://cse512-22sp.pages.cs.washington.edu/Metro-Innovation/#users)

- Boyuan then laid out the final design (~ 5 hours)

- Shruti refined the final design, setup the gitlab page and published the design on it (~ 6 hours)

- Mai helped drafted the initial version of the final poster (~ 1 hour)

- Shruti and Neha finished up the final version of the poster (~1 hour) and Mai submitted it. 

- Boyuan and Neha conducted a quick usability study using the "I like, I wish and what if?" framework (~2 hours each)

- Shruti put together this writeup with input from Boyuan and Neha (~ 2 hours)

### Challenges 

- Figuring out which encodings to use to communicate the relative rankings of the cities was challening. We tried bar graphs with joint interactions, aggregated data in different ways and tried a couple of different heat maps before we settled on what we have.

- Layout was extremely challenging. We had a lot of data and were trying to communicate complex information about a very complex process (namely innovation). So, the challenge was how to make sure that our visualization was both **_expressive and effective_**. I personally (Shruti) still believe we have a long way to go on this and got some great feedback from the survey and poster session. 

### Design Limitations

- We did not have enough time to fix the initial state of the pie charts. So, if all cities are picked instead of showing the total it just shows slices of the pie for all the cities separately. 

### Major Takeaways

- **Boyuan**: Learned more advanced skills in Tableau. Including creating parameters, creating dynamic choosing charts, linking multiple databases,creating and designing dashboards, and using navigation to hide and show charts etc. More importantly, I learned how to group multiple charts together to show the information more efficiently. 

- **Neha**: For previous assignments, I had mostly used the Altair or Plotly library features for visualization, but this time our team decided to use Tableau. I was able to create a preliminary design of the dashboard with the help of the tutorial and self-learning through internet resources. People who like to code, including myself, tend to make visualizations in Python or Javascript, but being able to use Tableau makes a lot of visualization easier and saves me time. 
I also learned how important data wrangling is when creating a good visualization. For the final project, we spent a significant amount of time gathering the necessary data and then customizing the data format to meet our design requirements. Next, we  created our initial dashboard on Altair, which took nearly 3 hours to create a basic map design, and then our team decided to design a dashboard with Tableau, which gave us a lot of flexibility in creating different types of visualization.
Another takeaway is that making a Tableau dashboard public using desktop Tableau is not straightforward as it may seems. As a first-time user, I had to use Google and watch a YouTube to make my Tableau dashboard public.

- **Shruti**: A major takeway for me was the realization that spending time figuring out the right question is half the work done. Once we have a solid idea of what we need the technical process of creating and deploying the visualization becomes much easier. We also created many prototypes and design alternatives. The power of rapid prototyping and how Tableau facilitated that very quickly was another takeaway for me. 

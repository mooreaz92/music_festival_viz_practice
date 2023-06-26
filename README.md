## Project Overview and Objectives

<div style="text-align:center">
    <img src="images/festival.jpg" style="width: 50%; border-radius: 10px;"/>
</div>

#### *Overview*

The following is a personal project where publicly available tables containing music festival data are web scraped, combined, cleaned, and visualized in Tableau.

#### *Objectives*

This project will have five main objectives:

1. Web scrape music festival data from Festival Alarm, a publicly available website that tracks music festival data (mainly in Europe)
2. Combine the scraped data into a single table
3. Perform a high-level analysis of the data and clean it as needed
4. Export the data to Tableau and create visualizations for publication
5. Document learnings and findings from the project

#### *A note on web scraping*

The Flatiron school data science boot camp teaches it's students to always check the terms and conditions of a website before web scraping. Festival Alarm does not have a terms and conditions page, but it does have a privacy policy page (however, it is in German, so this was translated using CHat GPT).

The privacy policy page does not explicitly state that web scraping is not allowed, but it does state that the website is not to be used for commercial purposes.I reached out to the website owners and waited a week for their response; none was given. Since this project is for educational purposes only and there is no explicit statement against web scraping, I decided to proceed with the project.

If anyone from Festival Alarm reads this and would like me to take down this project, please reach out to me and I will do so immediately. You can email me at mooreaz92@gmail.com or message me on GitHub.

**Website Overview**

The target website looks like this:

<div style="text-align: center;">
  <img src="images/website_screen_1.png" alt="Website Screen 1" width="40%" style="border-radius: 10px;">
</div>

The above example is for the year of 2023. In order to change years, you must click on the year in the top right corner of the screen. This will bring you to a page that looks like this:

<div style="text-align: center;">
  <img src="images/website_screen_2.png" alt="Website Screen 2" width="40%" style="border-radius: 10px;">
</div>

From here, you can click on the year you want to view and a table like the first screenshot will pop up. The table contains the following fields (I have added what I believe each field to mean in italics):

- Name 
  - *The name of the festival*
- Date + [year being viewed] 
  - *The date of the festival*
- Duration 
  - *The duration, in days, of the festival*
- Where 
  - *Whether the festival is indoors or outdoors*
- Category 
  - *The type of music played at the festival*
- Genres 
  - *The genres of music played at the festival*
- Country 
  - *The country the festival is located in*
- Visitors 
  - *The number of visitors the festival had*
- Price 
  - *The price of a ticket to the festival, in euros*
- Links 
  - *Links to the festival's website, ticket site, and an option to add to your festival list*

  To webscrape this data, I will use a combination of the `requests` and `BeautifulSoup` libraries. The `requests` library will be used to make the HTTP request to the website and the `BeautifulSoup` library will be used to parse the HTML and extract the data. High level, we will code a custom function that takes in a list of years and that does the following:

1. Makes an HTTP request to the website
2. Parses the HTML using `BeautifulSoup`
3. Extracts the data from the HTML
4. Returns the data in a list of dictionaries
5. Combines the list of dictionaries into a single dataframe

## Pivoting to using the GoogleMaps GeoCoding API

In the first draft of this project, we just had Tableau generate the latitude and longitude of each festival. However, as I learned in the certification course, Tableau is not great in identifying European locations beacuse of the various address formats used in Europe. I noticed, firsthand, that Tableau had a lot of difficulty interpreting the latitude and longitudes of European addresses. 

While this can't be easily done in Tableau Public, we can get some practice using the GoogleMaps API to get the latitude and longitude of each festival. We can then use this data to add a latitude and longitude column to the dataframe and get accurate locations for each festival.

## Final Visualization and Conclusion

#### The final visualization can be found [here](https://public.tableau.com/app/profile/ryan.moore6603/viz/FestivalAlarmDatabaseVisualization/FestivalAlarmDashboard).

<div style="text-align: center;">
  <img src="images/festival_map.png" alt="Website Screen 2" width="60%" style="border-radius: 10px;">
</div>

*Thoughts on the data*

- The data on the website is user submitted, so there is no guarantee that it is accurate.
- This is pretty readily apparant in the 'visitors' column, where some festivals have a visitor count of 0 and others have a visitor count of 500,000. When doing any kind of hard math over this data, it is important to keep in mind that the data is likely not accurate and would need to be verified before making any kind of business decision based on it.
- The data is also not very clean. There are a lot of null values and the data is not formatted in a way that is easy to work with. This is not surprising as the data is user submitted and there does not appear to be a rigorous vetting process for the data.
- The data is also not very consistent. For example, the 'Date' column is formatted differently depending on the year the festival took place. This makes it difficult to work with the data and requires a lot of cleaning before it can be used.

*Findings in the visualizations*

- The visualizations show that the majority of festivals take place in the summer months, which is not surprising.
- The visualizations also show that the majority of festivals take place in Germany; this is likely because the website is based in Germany and the majority of the users are from Germany.
- I was suprised to find that the majority of festivals are free. I would have thought that the majority of festivals would have a ticket price, but this is not the case. This is likely because the majority of festivals are small, local festivals that are free to attend.
- I was suprised to see that rock was the most represented genre in the data. I would have thought that electronic music or metal would have been the most represented genre due to my past experiences with European festivals. Also suprising was that pure rock festivals were not the highest attended festivals. However, due to the irregularity of the data, it is likely that this data is not accurate and would need to be verified.

*Webscraping*

- Webscraping with Beautiful Soup is a powerful tool for extracting data from websites, and is suprisingly easy to use. HTML code is super hard to read, but Beautiful Soup makes it easy to navigate through the code and extract the data you need.
- I will definitely be using this tool in the future for extracting data from websites when a formal API is not available. 
- I'm glad that the FLatiron bootcamp introduced me to this tool, but also taught me how to use it in a way that is not unethical. 
- I'm learning more and more about the foundations of all this great tech, and i'm suprised that so much of it is open source. There was so much open source collaboration in the past that chose innovation over profit, and I think that is a great thing. Webscraping is the first instance where there is more of a dialouge about the ethics of using the code to scrape websites. While I agree with the fundatmentals of collaboration, I also think that it is important to respect the wishes of the website owner. If they don't want you to scrape their website, then you shouldn't scrape their website.

*APIs*

- Man, for the longest time, the word API scared me. It was such a vague word and I didn't understand how it worked in practice
- However, after working with the GoogleMaps API, I have a much better understanding of how APIs work and how to use them.
- This is really promising, as i'm sure AI and ML will be using APIs to communicate with each other in the future. I'm glad that I have a better understanding of how they work now.

*Tableau*

- I'm really glad that I took the Tableau certification course. I learned a lot about how to use Tableau and how to create visualizations that are easy to understand and tell a story.
- However, in practice, with unclean data, it can be difficult to create visualizations that tell a story. I think that this is a good thing, as it forces you to think about the data and how to clean it in order to tell a story.
- It also *really* does not like European addresses. I had to use the GoogleMaps API to get the latitude and longitude of each festival in order to get accurate locations for each festival. This was a great opportunity to do some tangential learning and get some practice using the GoogleMaps API.
- There are certainly limitations when using one-hot encoded data in Tableau. For example, if you want to create a visualization that shows the number of festivals in each genre, you have to create a calculated field for each genre. This can be tedious and time consuming and not in the spirit of what I was hoping to get out of this project

## Next Steps

- I would like to create a more robust webscraper that can scrape the data from the website on a regular basis. This would allow me to create a database that is updated regularly and can be used to create visualizations that are more accurate.
- I would also like to continue build on the visualizations that I created in Tableau. I would like to create a dashboard that allows the user to filter the data by country, genre, and date. This would allow the user to get a better understanding of the festival landscape in Europe and make better decisions about which festivals to attend.
- I would also like to see if there is any way to verify the data on the website through use of some other APIs. This would allow me to create visualizations that are more accurate and can be used to make decisions about which festivals to attend.

## Using this Repository

- You are in the `README.md` file. This file contains the overview of the project and the objectives of the project. It also contains the final visualization and a link to the Tableau Public dashboard.
- The `index.ipynb` file contains the code used to webscrape the data from the website. It also contains the code used to clean the data, use the GoogleMaps API to get the latitude and longitude of each festival, and export the data to a CSV file.
- The `images` folder contains the images used in the `README.md` file.

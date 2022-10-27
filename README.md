## NHS wait times

Please note I've taken this project down while I'm refactoring it to a new version, but you can still check out the screenshots, features, and functionality of the v1 version below.

    
<img src="https://thehardgainerbible.com/wp-content/uploads/2022/08/nhs_app_alpha_1.png" width="800">
<img src="https://thehardgainerbible.com/wp-content/uploads/2022/08/nhs_app_alpha_3.png" width="800">  

[![has-fresh-nhs-data](https://github.com/ceefar/NHS_wait_times/actions/workflows/confirm_data_or_run_etl.yml/badge.svg?event=schedule)](https://github.com/ceefar/NHS_wait_times/actions/workflows/run_pytest_on_db_dataset.yml) [![create_v2_home_data](https://github.com/ceefar/NHS_wait_times/actions/workflows/create_v2_home_data.yml/badge.svg)](https://github.com/ceefar/NHS_wait_times/actions/workflows/create_v2_home_data.yml) [![create_daily_qa_data](https://github.com/ceefar/NHS_wait_times/actions/workflows/create_v2_qa_data_basic.yml/badge.svg)](https://github.com/ceefar/NHS_wait_times/actions/workflows/create_v2_qa_data_basic.yml)
  
### Personal Project [NEW] [Current] 
[ api | data-cleaning | etl | data-analysis | async | web scraping | mysql | python | streamlit | echarts | cicd ]   
  
### Summary
**Web app allows users to make informed decisions about their referrals based on wait times for every department at every hospital in England**  
  
- Speed optimised asyncronous ETL extracts large publicly available NHS datasets, cleans the data, and loads it to my own hosted database 
- Automatically creates historical trends table data when new data fom the ETL is loaded with MySQL triggers
- Coalesce multiple datasets in MySQL to ensure data consistency (if no data for avgWait first appt, fallback to avgWait for treatment)
- ETL performance timing TABLE A: total 44,616 items (4k+ rows) in under 0.6sec (extract, clean, load to hosted database)
- ETL performance timing TABLE B: total 482,783 items (4k+ rows) in 2.2sec (extract, clean, load to hosted database)
- Utilises a hidden NHS json API and some basic web scraping to pull inital data, + Google APIs for Geocoding and Maps functionality
- Various analysis and calculations on data to present accurate, insightful information to end users
- Currently in Alpha, quickly put together very basic functionality to explore a multitude of concepts, code needs to be optimised  
- Upcoming : refactoring project in /v2_alpha for improved structure, oop implementation, and db updated schema
   

  ### NEW - CI/CD Implementation   
**Ensures fresh NHS data from the hidden API is cooked up once a day, trigger creation of historical data, creates new data with improved schema with ctes, runs unittests, runs quality assurance**  
  
- Maintains uptime and stays operational without any manual need to load the web app to run the etl which pulls the live data  
- Pytest GitHub actions ensures data completeness is at acceptable standard (for using the app)  
- New Pipeline to create aggregated data for new concept home page with improved schema  
- **NEW** - Custom coloured logs during CICD Quality Assurance Processes (+ DB storage)  
<img src="https://github.com/ceefar/NHS_wait_times/blob/main/readme_imgs/clean_af_cicd_qa_logs.png" width="400">  
  
### NEW - Compare  
Compare two hospitals in the country to see their overall performance vs either countrywide or regional averages   
  
<img src="https://thehardgainerbible.com/wp-content/uploads/2022/09/nhs_new1.png" width="800">  
  
### NEW - Historical Trends
Automatically creates and updates the historical data table through mysql triggers, including tally visualisation of historical trends over the current week, month, and all time   
  
<img src="https://thehardgainerbible.com/wp-content/uploads/2022/08/nhs_trends_1.png" width="800">
    
### NEW - Use Case Implementation
Use case page [alpha - old screenshots] - allows users to select departments they have been referred to, to get personalised specific information and actions to take based on efficiency of selected hospital, with stats broken down by region and for the entire country

<img src="https://thehardgainerbible.com/wp-content/uploads/2022/08/nhs_app_alpha_2_1.png" width="800">

<img src="https://thehardgainerbible.com/wp-content/uploads/2022/08/nhs_app_alpha_2_2.png" width="400"><img src="https://thehardgainerbible.com/wp-content/uploads/2022/08/nhs_app_alpha_2_3.png" width="400">
  
   
-----
  
### COMING SOON   
### v2_Concept  
**Upgraded UI + Updated Schema + Functionality & Optimisation Refactor**   
Currently ongoing refactor to create a drastically improved codebase (cleaner code, class based structure, ci/cd, upgraded schema, stronger emphasis on best practices, greater logging & qa, optimisations, etc).  
The primary aim being to significantly improve webapp load times (current speed optimisations approx 5-10x), as well as update the ui to a much more impactful, modern day design and implement app-wide ux upgrades.  

<img src="https://github.com/ceefar/NHS_wait_times/blob/main/v2_home_concept_preview.png" width="800">
  
### Project Roadmap - [not ordered]

- Improve the ETL to parse the monthly dataset raw, & to download the new monthly dataset each month automatically *[etl improvements]*
- Add true data visualisations to Historical Trends page
- More actionable information and inputs for referrals for use case page *[page improvements]*
- Speed improvements more async, general optimisations *[optimisation]*
- Improve implementation of software engineering standards and principles 
- IaaC to create offline data each day and store in it a local server, spun up via docker *[iaac]*  
- Social sharing, image creation and sharing, data/info export *[page improvements]*
- Sign up for email based updates on given hospital or department *[functionality]*
- Make the week breakdown dataset (482,783 items) etl run asyncronously *[etl improvements]*
- Create a discord chatbot for QA data analysis *[webhooks]*
- Submit project to streamlit monthly rewind *[pre-launch/launch]*
- Stress testing the web app with a soft beta launch, making web app readily available for media sources and testers *[pre-launch/launch]*
- Officially launch and promte the web app for use by the public, primarily targeting adoption for those who need it most *[pre-launch/launch]*  
  
   
**COMPLETED / IN-PROGRESS / ONGOING**  
- **[ON-GOING]** Update screenshots in readme to showcase new features and functionality *[ongoing/documentation]*
- **[ALPHA]** Adding 'Department Detailed View' page *[new page]*
- **[ALPHA]** Implement unit tests (pytest) and basic CI/CD *[dev ops]*
- **[ALPHA]** Furthering the level and detail of analysis in the homepage *[page improvements]*
- **[ALPHA]** Deep Historical information from new dataset based on 12 years of referal *[new page]*
- **[BETA]** View the historical trends in a visualised table [new page]
- **[DONE]** Automatically logs historical trends data in a separate table through MySQL triggers [data expansion]
- **[DONE]** Implement the new 482k dataset into data within one of the new pages *[page improvements]*
- **[DONE]** Expanded the dataset to include the weekly breakdown data, so now 2 sets of etl data from raw sources - 44k+ items and 482k+ items *[data expansion]* 
- **[DONE]** Expanding the dataset to utilise the official NHS CSV. A total of 44,616 items so will require an ETL to clean and load the data to my own database before transforming it for web app display based on user queries. Also allowing for greater tracking of historical changes in the data. *[data expansion]*
- **[DONE]** Expanding the dataset with coalesce to include secondary wait time data, which will serve as a backup when first appointment data is not available *[data expansion]*
- **[DONE]** Implement echarts functionality in streamlit *[functionality]*
- **[DONE]** Use case page which is detailed properly above *[new page]*
  
  
#### GitHub Stats   
![Ceefar's GitHub stats](https://github-readme-stats.vercel.app/api?username=ceefar&show_icons=true&theme=gruvbox)   

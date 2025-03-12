# webscraper

Below is a summary of the weather data web scraper project:

---

### Project Summary: Weather Data Web Scraper

This project implements a Python web scraper to extract historical weather data from [weatherforyou.com](https://www.weatherforyou.com). The scraper is designed to work over a specified date range and collect detailed weather information for each day within that range. Below are the key components and steps of the scraper:

1. **Date Range Definition:**
   - The scraper uses the `datetime` module to define a start and end date. In this case, the dates are set from October 24, 2019 to October 31, 2019.
   - A list of dates is generated using `timedelta` to iterate over each day in the specified range.

2. **URL Construction and Data Retrieval:**
   - For each date, the code dynamically constructs a URL to request the historical weather data for a specific location (**San Francisco, CA, with zipcode 94102**) on that date.
   - The `requests` library is used to send HTTP GET requests to the constructed URL.
   - The scraper includes basic error handling to check the status code of the response and skips any dates that fail to return a successful response.

3. **HTML Parsing and Data Extraction:**
   - The retrieved HTML content is parsed with `BeautifulSoup`.
   - The code searches for a specific header cell with the class `"IntWxHeader"` to locate the nested table containing the weather data.
   - Once the target table is identified, all rows (except the header row) are processed.
   - For each row, the text content is extracted from `<span>` elements that match a particular style (i.e., font size 16px), and the current date is appended to the row data.

4. **Data Aggregation:**
   - All the extracted rows are stored in a list.
   - On the first successful extraction, the code also captures the header row from the HTML to form column names and appends an extra "Date" column.
   - After processing all dates, the collected data is converted into a pandas DataFrame with the proper headers.

5. **Additional Features:**
   - A progress bar is displayed using the `rich` library to provide feedback during the scraping process.
   - A short pause (`time.sleep(0.5)`) is added between requests to avoid overwhelming the server.
   - The final DataFrame is printed, and it can optionally be saved as a CSV file for further analysis.

---

This web scraper demonstrates an end-to-end process of data extraction from a dynamic website, from URL construction and HTTP requests to HTML parsing and data aggregation, culminating in a structured dataset ready for analysis.

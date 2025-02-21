# Gold-Trade

1) Abstract:
This research provides the importance of gold trade imports from the reporting countries such 
as South Africa, Kenya and Egypt focusing on relation between the BRICS countries and other nations. 
This analysis completely relies on the data from the UN ComTrade database on the periods from 2017 
to 2023 which signifies the pre-covid, covid and post-covid of gold trade data between countries. This 
study evaluates various data methodologies on the gathered data to make it readiness for meaningful 
insights and help the experts to understand how gold has been influencing the markets around the 
world. Gold has become a prominent way of trade without the use of US dollars, and this study explores
how the BRICS nations are conducting this trade worldwide which paves the way for emerging the new 
currency. These findings assess how this new currency becomes the revolutionary and grows fast among 
the countries for trade around the world. The insights on various trends over the volume and price helps 
the professionals understand why there is a sudden change in the market in recent years. Gold Trade
on various years has been performed from various directions understanding how prominent the market 
evolved currently and helps the countries grew fast more economical. This also considers on how the 
dominant countries fall and offers more meaning forecasting insights about the future.
Keywords: Gold trade, UN Comtrade, BRICS nations, Emerging Currency, Market Analysis, Trend 
Analysis, Price, Quantity, Import, Export, South Africa, Kenya and Egypt
2) Introduction:
This study explores the impact on the US dollar resulting from gold trade exports between BRICS 
countries and other nations. This focuses on reporters such as South Africa, Kenya, and Egypt data that 
are readily available to us. The data has been sourced from the UN ComTrade database, via API with 
frequent data updates. Since the data has taken from free version with certain parameters which 
consists of aggregated results to a certain degree (AGGR_LEVEL = 4/6) rather than open bulk data. This 
makes the data less accurate and faulty results. Hence, to make quality of the content, this study does 
not consider any historical or future predictions of the data and consider only the current data from 
2017 to 2023. That covers the periods such as before, during, and after COVID-19, with each period span 
of two years. Due to the limitations of the free version of the UN ComTrade data, additional data 
handling methods were used to get proper analysis results.
2.1) What is BRICS?
BRIC is known for Brazil, Russia, India, China which is formed in 2009, and in 2010 the South 
Africa was added, forming five major economics in the world. The concept of BRICS is proposed in 2001 
by Jim O’Neill, and the first official meeting which is held by five nation leaders Yekaterinburg Russia in 
UE, Potsdam Group 3 PS24 Data Science and Business Pg 4
2009 and in December 2010 south Africa was invited to join the group then the name changes from BRIC 
to BRICS, which enhance its geopolitical influence [1].
2.2) Why are BRICS nations formed?
The BRICS nations aim to grow their economy by co-operation, mutual trade and mutual 
investment. The key objective of formation was to reform the international financial institutions like 
World bank and International Monetary Fund (IMF) which is dominated by western nations [2].
2.3) What is BRICS currency?
The concept of BRICS currency has been circulated around the five nations such as Brazil, Russia, 
India, China and South Africa. The main objective of the BRICS currency is to create and promote a new 
financial system in gold trade among global markets. The evolution of new BRICS currency will reduce 
the usage of US dollar in the global gold trade. In recent days, trade system has been evolved to reach 
its peak of 100% by prominent US dollars which paved the way for United states to influence the global 
financial systems. 
The BRICS currency is backed by the pool of five nation currencies which is Brazilian Real, Russian 
Ruble, India Rupee, Chinese Renminbi, and South African Rand which refers to R5 or R5+ currency [3]
and this idea includes a backing element in the form of commodities such as Gold to promote additional 
security for the new currency [4].
There is no sign of implementations of the BRICS currency yet, but the process of evolution 
continues to grow and gets updated in the future BRICS summits. The main theme of 2023 summit was 
to discuss on upbringing the BRICS currency, but it has not been released yet. 
2.4) Impact on US Dollars by BRICS Currency
As of now the traditional method to trade international transactions are held in US Dollars. In 
the year 2023, the BRICS nations discussed about creating new currency that are backed by gold paving 
the way to the evolution of BRICS currency. This BRICS currency will completely change the global 
transactions trade which is held in US dollars. As a first step, BRICS are introducing a new currency by 
masking “de-dollarization” which will impact enormously on US dollars.
The US dollars is prominent as world primary reserves for decades. This process of dedollarization is complex; to bring it in effect as the BRICS need the reliable payment systems by 
considering all the problems that may arise as the BRICS nations continues towards de-dollarization to 
decrease the dependence on US dollars [5].
The economic consequences for the United States will make impact on economic adjustments 
UE, Potsdam Group 3 PS24 Data Science and Business Pg 5
within the United States. The main advantage of this BRICS currency to reduce the conversion costs for 
the trade among the member nations more efficiently [6].
3) Methods:
The research on the gold trade exports has been conducted with the various techniques and 
methods such as below:
3.1) Data Preprocessing:
The source data has been processed based on the data wrangling techniques such as below:
3.1.1) Data Availability:
The source data for this research has been taken from the UN ComTrade database. The data has 
been obtained from source through the API by passing the below parameters:
Freqcode = M #Monthly
ClsCode = HS #HS Classification
Period = 2017 to 2023
ReporterCode = 404, 710, 818 #Kenya, South Africa, Egypt
CmdCode = 7108, 710811, 710812, 710813, 710820 #Gold
FlowCode = X #Export
3.1.2) Data Analysis:
Based on the “Mapping Document.xlsx” workbook [mentioned in Appendix 1], data analysis has 
been conducted to the access data via API calls and the data has been filtered based on given criteria 
mentioned under “Assumptions” column in “Mapping” Sheet. The raw source data extracted via API is 
archived in the data lake table named as “GOLD_TRADE_DL”
3.1.3) Data Transformation:
For certain attributes with similar values, data transformation has been performed so that the final 
records contain only non-zero/non-null values for the mandatory columns and sent for further 
processing. Below are the conditions listed for the transformation:
i. Primary Value: This attribute defines the trade value in dollars. The records with the trade 
value such as blank, or null values are considered as invalid. In such conditions, the 
UE, Potsdam Group 3 PS24 Data Science and Business Pg 6
corresponding value is copied directly from the FOB_VALUE, as FOB_VALUE contains exact 
export values.
ii. Net Weight: This attribute defines the trade volume in kilograms. The records with the trade 
volume such as blank, or null values are treated as invalid. In such cases, data has been
compared with Qty and AltQty attributes. If the value is in grams, data has been converted 
and then copied to NetWeight in Kilograms as we are dealing with only grams and kilograms 
data from the source.
3.1.4) Data Mean Substitution:
For certain records, we have identified that the data has been missing or as 0 for the required 
attributes. In such cases, to avoid loss of data, data has been filled with mean values from the other 
months for the reporters which makes the data consistent while plotting for visualization.
3.1.5) Data Outliers Handling:
As we are dealing with the real-time data with combination of reported and aggregated values, 
there is a high possibility that data may fall on invalid range which makes the visualization inconsistent. 
To avoid such issues, z-score outliers has been performed by calculating the relation between the 
important attributes and then those records are removed which makes the data ready for visualization.
3.1.6) Data Validation:
After analyzing the data, there are lot of duplicates found on basis of aggregated values. To 
clean those duplicate sum values, data validation has been performed using “Data Validation.xlsx” 
[mentioned in Appendix 2]. Records that fail to satisfy the conditions are rejected and stored in the 
reject table named as “GOLD_TRADE_DATA_REJECT “. Records that met the conditions are stored in the 
data warehouse table named as “GOLD_TRADE”, with the final columns listed in the requirement 
document.
3.1.7) Data Readiness:
To visualize the data, not all the attributes mentioned in the requirement specifications are 
required. Hence, unwanted attributes are removed and are stored in the data mart table named as 
“GOLD_TRADE_DATA_MART”.
UE, Potsdam Group 3 PS24 Data Science and Business Pg 7
3.2) Other Data Sources:
Historical standard gold prices for comparison are collected from world bank [7], then converted 
from oz to the kilograms and stored in the table named “GOLD_PRICE”.
Information that are related to the BRICS countries are sourced from Wikipedia [8] and then 
updated with Partner data taken from ComTrade, stored in the table named “BRICS_CONT”

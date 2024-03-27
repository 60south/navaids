# navaids
A list of USA aviation Navigational Aids (NAVAIDs), including VORs, VOTs, and VORTACs.

*This dataset is provided with no guarantees of accuracy or completeness whatsoever. Use at your own risk.*

----

For additions, deletions, corrections or suggestions, please create an "Issue". For new stations, the minimal information necessary is:
- The station identifier, usually a three letter FAA ID, e.g.: "BUF"
- The plain English name of the station (e.g., "Buffalo")
- Latitude and longitude in decimal degrees

Recommended addtional information:
- Elevation in feet
- Frequency

----
Additional US and international NAVAIDs might be found at: 
- https://adds-faa.opendata.arcgis.com/datasets/990e238991b44dd08af27d7b43e70b92_0/explore?location=9.874507%2C-1.658582%2C1.93
- https://www.faa.gov/air_traffic/flight_info/aeronav/aero_data/NASR_Subscription/ (click on the current or past subscriptions, and look for a zipped NAVAID file link)
- https://www.dxmaps.com/callbook/index.html

Some navigational aids may be listed in the stations list at: https://aviationweather.gov/data/api/

Independent validation or refinement of the NAVAIDs listed here may come from: https://www.airnav.com/navaids/

----
### Notes

On Fri, Mar 22, 2024 at 10:54 AM Glenn Grant <aviationweather.webmail@noaa.gov> wrote:

Name: Glenn Grant

Category: Question

Subject: Need a complete list of NAVAIDs with lat/lon

Hi. I'm trying to use CWAs downloaded from the Data API to chart out locations of advisories. To do this, of course, I need the lat/lon locations of the NAVAIDs specified in the "FROM" line of each CWA.

I found the list of stations (JSON format) at the end of the API web page, but it appears incomplete. For instance, the CWA on 20240316_0000Z includes:
```
Hazard: ICE
FAUS23 KZAB 152313
ZAB3 CWA 152311 
ZAB CWA 301 VALID UNTIL 160111
FROM 45ENE DRK-30S INW-75SSE INW-70ESE PHX-25SSW PHX-50NW PHX-30SW 
DRK-45ENE DRK
AREA MOD/SEV ICE 090-FL190. RPRTD BY ACFT. ..ADDN INFO TO SIGMET.. AZ
```
Referring to the list of NAVAIDs, I can find Pheonix (PHX) and Winslow (INW), but not the Drake VORTAC in Prescott, AX (code DRK). 

Is there a list somewhere that includes *all* of the NAVAIDs referenced in CWAs and PIREPs?

Thanks!

----

Hi Glenn,

Thanks for reaching out. This turns out to have a complicated answer with a couple of moving parts.

The first part is that the FAA provides most of the information about NAVAIDs. You can download it here: https://www.faa.gov/air_traffic/flight_info/aeronav/aero_data/NASR_Subscription/

Another good data source from the FAA is their GIS page: https://adds-faa.opendata.arcgis.com/

The NASR files are not necessarily in a user-friendly format for what you're looking to accomplish. I know this firsthand because I've been working on a research project involving plotting domestic SIGMETs, and those products use a similar location specification as the CWAs (distance and bearing from a reference point). I, too, expected to find a simple list somewhere containing station IDs and lat/lons. I'll save you about 20+ hours of online searching-- the answer is that the FAA does not provide such a list. You'll have to construct it yourself by parsing the FAA files to extract what you need. 

The next part is that the FAA updates those navigation aids every 28 days. In order to plot a CWA or a domestic SIGMET, you need to have the values for lat/lon and IDs that were valid at the time the product was issued. This means that you can't use today's file to plot CWAs from 3 months or 5 years ago. Depending on the exact date, you might not be able to use it for a CWA from yesterday or last week. There is a short archive available on the FAA's website if you need the NASR files from the past couple of months. 

Another consideration is that the FAA has been progressively decommissioning VOR locations over the last few years. They have a planned phase-out schedule, although minor adjustments sometimes occur. It is part of a broader modernization plan. Check the FAA website for details. Here's why that matters-- even though many VOR sites have already been phased out, they are still being used as location identifiers in some aviation products. Whether or not that should be happening is a different discussion, but the fact remains that those points are still being used at times.

Hope that helps.

Kind regards





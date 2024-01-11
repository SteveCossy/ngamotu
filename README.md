# Ngāmotu Penguin Data
## Introduction
|  |  |
|----|----|
|  Data here is coming directly from the Raspberry Pi computer which acts as a [gateway on a colony of Kororā](https://drive.google.com/file/d/1U8EknLFfSr9mckw2uGNsGBZ0HN9ohxNW/view) near New Plymouth.  [The project, Finding Little Blue, is documented here](https://www.citscihub.nz/Finding_Little_Blue).<p>The data is gathered from sensors in and around Kororā burrows. | ![Finding Little Blue logo](https://citscihub.s3.amazonaws.com/flb_logo.png)

## Data Structure
The filenames above identify the site, then the channel number, as received from the Burrow Sensors in the [site diagram](https://drive.google.com/file/d/1U8EknLFfSr9mckw2uGNsGBZ0HN9ohxNW/view).  There is also a Quality of Service measure which sends an error count to channel 25 every five minutes.
* 'Mouse over' a filename to see the channel number.
* Click on a file name to download all the data for a channel.  This can be downloaded or copied and pasted into a spreadsheet.
* Click on any date and time and you can look at **all** the data uploaded over the hour leading up to that time.  
## Channel Numbers
| Ch | Device | Mound | Nest | Unit   | Notes |
| -- | ----- | ----- | ---- | ------ | ------ |
| 1  | test  |       |      |        | |
| 2  | test  |       |    |        | |
| 2  |       |       | 14   |        | |
| 3  |       |       | 9    |        | |
| 4  |       |       | 8    |        | |
| 5  |       | 2     |      | mVolts | |
| 6  |       |       | 20   |        | |
| 7  |       |       | 21   |        | |
| 8  |       |       | 19   |        | |
| 9  |       |       | 11   |        | |
| 10 |       | 4     |      | mVolts | |
| 11 |       |       | 7    |        | Sometimes fails checksum |
| 12 |       |       | 6    |        | |
| 13 |       |       | 5    |        | |
| 14 |       |       | 4    |        | |
| 15 |       | 1     |      | mVolts | |
| 16 |       |       | 10   |        | |
| 17 - 19 | test  |       |      |        | |
| 17 |       |       | 16   |        | |
| 18 |       |       | 15   |        | |
| 19 |       |       | 18   |        | Always fails checksum |
| 20 |       | 3     |      | mVolts | |
| 20 - 25 | test  |       |      |        | |
| 22 | test  |       |      |        | |
| 23 |       | | | QOS | Good Packets ASK data (nbr pver 5 minutes) |
| 24 |       | | | QOS | Bad Packets |
| 25 |       | | | QOS | Good Packets Serial interface |
| 26 |       | | Battery Voltage | mV | |
| 27,28 | test  |       |      |        | Sometimes fails checksum |
| 29 | test  |       | 16   |        | Always fails checksum |
| 30 |       | RFID Status |      | | 3 digits is charging rate, 4 digits RFID tuning, 5 digits = mlvots of 12V battery |
| 31 |       | | 6 | RFID | |
| 32 |       | | | RFID | |
| 33 |       | | 10 | RFID | Last entry 2024-01-09T15:29 |
| 34 |       | | 10 | RFID | Only entry 2024-01-08T11:13 |
| 51-55 | test |       |      |        | |
| 132 |       |       | 16   | RFID? | values registered: 86 94 47 16443 32859 |

## Technical Description
|  |  |
|----|----|
| crontab-root | Crontab for root on the Pi, which reboots every afternoon at 1pm. |
| crontab-pi | Restarts the Serial to CSV python script on reboot. Runs CSV-GIT every ten minutes |
| Serial_to_CSV.py | Reads any data coming in the serial port and writes it to a CSV file in /home/pi/ngamotu |
| CSV-GIT.sh | Updates this files listed above with the contents of /home/pi/ngamotu |

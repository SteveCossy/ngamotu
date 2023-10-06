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
| Ch | Mound | Nest | Unit   |
| -- | ----- | ---- | ------ |
| 1  |       |      |        |
| 2  |       | 14   |        |
| 3  |       | 9    |        |
| 4  |       | 8    |        |
| 5  | 2     |      | mVolts |
| 6  |       | 20   |        |
| 7  |       | 21   |        |
| 8  |       | 19   |        |
| 9  |       | 11   |        |
| 10 | 4     |      | mVolts |
| 11 |       | 7    |        |
| 12 |       | 6    |        |
| 13 |       | 5    |        |
| 14 |       | 4    |        |
| 15 | 1     |      | mVolts |
| 16 |       | 10   |        |
| 17 |       | 16   |        |
| 18 |       | 15   |        |
| 19 |       | 18   |        |
| 20 | 3     |      | mVolts |
| 30 | RFID Status      |      | (Very good question) |
| 31 | | 6 | RFID |
| 32 | | | RFID |
| 33 | | 10 | RFID |

## Technical Description
|  |  |
|----|----|
| crontab-root | Crontab for root on the Pi, which reboots every afternoon at 1pm. |
| crontab-pi | Restarts the Serial to CSV python script on reboot. Runs CSV-GIT every ten minutes |
| Serial_to_CSV.py | Reads any data coming in the serial port and writes it to a CSV file in /home/pi/ngamotu |
| CSV-GIT.sh | Updates this files listed above with the contents of /home/pi/ngamotu |

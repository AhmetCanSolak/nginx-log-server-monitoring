# Nginx Log Server Monitoring
A sample program to parse and visualize important figures from nginx logs. [Demo report](http://www.cansolak.com/nginx-log-server-monitoring/results/report/report.html).

Project implemented as two separate parts.
1) Read, parse, process and append the each log to the DB. This part is implemented in C++.
2) Fetch the relevant information from DB and generate HTML report with related figures and visualizations. This part is implemented in Python.

## Usage
-Install dependencies with `sh install.sh`

-Run the program with `sh run.sh`

System Used in development:

* Ubuntu 16.04 LTS
* GCC/G++ 7.1.0
* Python 3.6.5

Dependencies:
* PostgreSQL-9.6,
* PostgreSQL-contrib-9.6,
* Libpqxx 4.0.1+dfsg3
* Psycopg2
* Matplotlib

## File Structure
`--->data/

------->nginx.access.log*                        -You should put your data file in here with this name given

------->sample.log                               -Single line sample from the log

--->lib/

------->libpqxx 4.0.1+dfsg3

------->matplotlib

--->results/

----->data/                                      -This is where histograms.txt and numeric_values.txt files are. Final 
information gathered from the log is in them

----->images/                                    -This is where .png files of charts

----->report/                                    -This is where the final HTML/CSS report is. After you run successfully open the report.html from here.

--->src/

----->cc/

------->dbFunctions.cpp                          -This is where DB related functions implemented

------->dbFunctions.h                            -This is the interface for dbFunctions.cpp

------->helperFunctions.cpp                      -This is where helper functions implemented

------->helperFunctions.h                        -This is the interface for helperFunctions.cpp

------->loadLogToDB.cc                           -This is the main function to load logs into database and visualize them in a report.

----->py/

------->charts.py                                -This is the python script where different ready-to-user chart creating functions are

------->reports.py                               -This is the python script all images and information gathered and reported into a .html file

------->visualize.py                             -This is the python script to fetch logs and visualize them in charts

->install.sh

->overview.txt

->run.sh
`

## Further Ideas:
-Bulk insert implementation for commitToDB function to have better performance in populating database.

-Trying to use getchar_unlocked() for a better reading performance, in case we do not care thread safety.

-Trying to use a read buffer for a better general performance

-Reading files in parallel :)


## References

* [PostgreSQL tutorial of Digital Ocean](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-postgresql-on-ubuntu-16-04)
* [C/C++ adaptor tutorial of Tutorials Point](https://www.tutorialspoint.com/postgresql/postgresql_c_cpp.htm)
* [Python adaptor tutorial of Tutorials Point](https://www.tutorialspoint.com/postgresql/postgresql_python.htm)
* [One Page Wonder Bootstrap Template](https://github.com/BlackrockDigital/startbootstrap-one-page-wonder)

## Copyright

All data and logo used to demonstrate sample report is provided by [Er Stream CDN Company](http://www.erstream.com/).

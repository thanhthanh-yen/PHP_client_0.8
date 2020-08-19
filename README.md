GridDB PHP Client

## Overview

GridDB PHP Client is developed using GridDB C Client and [SWIG](http://www.swig.org/) (Simplified Wrapper and Interface Generator).


## Operating environment

Building of the library and execution of the sample programs have been checked in the following environment.

    OS:              CentOS 7.8(x64)
    SWIG:            4.0.0
    GCC:             4.8.5
    PHP:             7.4.7
    GridDB Server:   4.5 (CE)
    GridDB C Client: 4.5 (CE)

## QuickStart
### Preparations

Install SWIG as below.

    $ wget https://prdownloads.sourceforge.net/swig/swig-4.0.0.tar.gz
    $ tar xvfz swig-4.0.0.tar.gz
    $ cd swig-4.0.0
    $ ./configure
    $ make
    $ sudo make install

    Note: If CentOS, you might need to install pcre in advance.
    $ sudo yum install pcre2-devel.x86_64

Install PHP7.4.7 and GridDB C Client.

Set LIBRARY_PATH.

    export LIBRARY_PATH=$LIBRARY_PATH:<C client library file directory path>

### Build and Run

    1. Execute the command on project directory.

    $ make

    2. Include 'griddb_php_client.php' in PHP.

### How to run sample (with Command Line)

GridDB Server need to be started in advance.

	1. Write the following desctiption in /etc/php.ini.

	    extension=<PHP client library file directory path>
	
    2. Set LD_LIBRARY_PATH.

        export LD_LIBRARY_PATH=${LD_LIBRARY_PATH}:<C client library file directory path>

    3. The command to run sample

        $ php sample/sample1.php <GridDB notification address> <GridDB notification port>
            <GridDB cluster name> <GridDB user> <GridDB password>
          -->Person: name=name02 status=false count=2 lob=ABCDEFGHIJ

### How to run sample (with Web Browser)

GridDB Server need to be started in advance.

In the case of Web Server: Apache/2.4.6, please use the following steps.

    1. Store griddb_php_client.php and sample/sample1_web.php in /var/www/html.

    2. Store griddb_php_client.so in /usr/lib64/php/modules.

    3. Add extension for griddb_php_client.so in /etc/php.ini

    4. Set LD_LIBRARY_PATH.

        export LD_LIBRARY_PATH=${LD_LIBRARY_PATH}:<C client library file directory path>

    5. Restart httpd/apache.

    6. In web browser, run : http://localhost/sample1_web.php.

    7. Click submit button after entering address, port, cluster, user and password.

## Function

(available)
- STRING, BOOL, BYTE, SHORT, INTEGER, LONG, FLOAT, DOUBLE, TIMESTAMP, BLOB type for GridDB
- put single row, get row with key
- normal query, aggregation with TQL

(not available)
- Multi-Put/Get/Query (batch processing)
- GEOMETRY, Array type for GridDB
- timeseries compression
- timeseries-specific function like gsAggregateTimeSeries, gsQueryByTimeSeriesSampling in C client
- trigger, affinity

Please refer to the following files for more detailed information.
- [PHP Client API Reference](https://griddb.github.io/php_client/PHPAPIReference.htm)

About API:
- When an error occurs, an exception GSException is thrown.

## Community

  * Issues
    Use the GitHub issue function if you have any requests, questions, or bug reports.
  * PullRequest
    Use the GitHub pull request function if you want to contribute code.
    You'll need to agree GridDB Contributor License Agreement(CLA_rev1.1.pdf).
    By using the GitHub pull request function, you shall be deemed to have agreed to GridDB Contributor License Agreement.

## License

  GridDB PHP Client source license is Apache License, version 2.0.

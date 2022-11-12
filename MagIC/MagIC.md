# MagIC database and file formats

A number of the programs in **PmagPy** were developed to take advantage
of the MagIC database and aid getting data in and out of it. So, we need
some basic understanding of what MagIC is and how it is structured.
MagIC is part of the EarthRef.org collection of databases and digital
reference material. Anyone interested in the MagIC database should first
become a registered EarthRef.org user. To do this, go to
<http://earthref.org> and click on the **Register** link in the
**Topmenu**. Registration is not required for access to data or browsing
around, but is required for uploading of data into the MagIC database,
something which we sincerely hope you will have a chance to do. After
you register, go to <http://earthref.org/MAGIC/search>.

You can [download data](#magic_download) using the [MagIC
search](http://earthref.org/MAGIC/search) website. After downloading,
the data can be unpacked and examined using various tools in the
**PmagPy** package, for example using [Pmag GUI](#pmag_gui.py).

Paleomagnetic and rock magnetic data are collected and analyzed in a
wide variety of ways with different objectives. Data sets can be
extremely large or can be the barest boned data summaries published in
legacy data tables. The goal of MagIC has been to have the flexibility
to allow a whole range of data including legacy data from publications
or other databases to new studies which include all the measurements,
field photos, methodology, and so on. The general procedure for the
future will be to archive the data at the same time that they are
published. So, to smooth the path, it is advisable to put your data into
the MagIC format as early in the process as possible. All data that
enters the database must be converted to the standard MagIC format
either as a set of MagIC tables, or as one combined text file. These can
then be uploaded into the MagIC database.

## Structure of the database tables

The MagIC database is organized around a series of data tables. The
complete data model can be found here:
<https://www2.earthref.org/MagIC/data-models/3.0>

The first line of each MagIC table looks something like this:

```tab table_name``

“tab” (or “tab delimited”) means that the table is tab delimited. In
theory other delimiters are possible, but **PmagPy** only uses tab
delimited formats. The **table_name** must be one of these nine table
names.

| table            | Brief description                                                                                 |
| ---------------- | ------------------------------------------------------------------------------------------------- |
| **contribution** | study metadata                                                                                    |
| **locations**    | location level data                                                                               |
| **sites**        | site level data, including geographic information, site averages of sample data, etc.             |
| **samples**      | sample level data, including orientation, sampling methods, sample averages of specimen data etc. |
| **specimens**    | specimen level data, including interpretations of best-fit lines, planes, paleointensity, etc.    |
| **measurements** | measurement data used in the study                                                                |
| **ages**         | age information.                                                                                  |
| **criteria**     | criteria used in study for data selection                                                         |
| **images**       | images associated with the study                                                                  |

The second line of each MagIC table contains the column headers
(meta-data) describing the included data. For example, a **sites** table
might look like this:

```{eval-rst}
================= ======== =========== ============== ===== ======
tab2em\ **sites**
site              location lithologies geologic_types lat   lon
AZ01              Azores   basalt      lava flow      37.80 -25.80
...
================= ======== =========== ============== ===== ======
```

Although data can be entered directly into Excel spreadsheets by hand,
it is easier to generate the necessary tables as a by-product of
ordinary data processing without having to know details of the meta-data
and method codes. The section on [PmagPy](#PmagPy) describes how to
use the **PmagPy** software for data analysis and generate the MagIC
data tables automatically for the most common paleomagnetic studies
involving directions and/or paleointensities. See also [Pmag
GUI](#pmag_gui.py).

## A word about method codes

The MagIC database tags records with “method codes” which are short
codes that describe various methods associated with a particular data
record. The complete list is available here:
<https://earthref.org/MagIC/method-codes>. Most of the time, you do not
need to know what these are (there are over a hundred!), but it is
helpful to know something about them. These are divided into several
general categories like ‘geochronology methods’ and ‘field sampling
methods’. Method codes start with a few letters which designate the
category (e.g., GM or FS for geochronogy and field sampling
respectively). Then there is a second part and possibly also a third
part to describe methods with lesser or greater detail. This table lists
method codes describing various lab treatment methods to give you a
flavor for how the codes work:

```{eval-rst}
+-------------+---------------+--------------------------------------+
| LT-AF-D     | Lab Treatment | Alternating field: Double            |
|             |               | demagnetization                      |
+-------------+---------------+--------------------------------------+
|             |               | with AF along X,Y,Z measurement      |
+-------------+---------------+--------------------------------------+
|             |               | followed by AF along -X,-Y,-Z        |
|             |               | measurement                          |
+-------------+---------------+--------------------------------------+
| LT-AF-G     | Lab Treatment | Alternating field: Triple            |
|             |               | demagnetization                      |
+-------------+---------------+--------------------------------------+
|             |               | with AF along Y,Z,X measurement      |
+-------------+---------------+--------------------------------------+
|             |               | followed by AF along Y and AF along  |
|             |               | Z measurement                        |
+-------------+---------------+--------------------------------------+
| LT-AF-I     | Lab Treatment | Alternating field: In laboratory     |
|             |               | field                                |
+-------------+---------------+--------------------------------------+
| LT-AF-Z     | Lab Treatment | Alternating field: In zero field     |
+-------------+---------------+--------------------------------------+
| LT-CHEM     | Lab Treatment | Cleaning of porous rocks by chemical |
|             |               | leaching with HCl                    |
+-------------+---------------+--------------------------------------+
| LT-FC       | Lab Treatment | Specimen cooled with laboratory      |
|             |               | field on                             |
+-------------+---------------+--------------------------------------+
| LT-HT-I     | Lab Treatment | High temperature treatment: In       |
|             |               | laboratory field                     |
+-------------+---------------+--------------------------------------+
| LT-HT-Z     | Lab Treatment | High temperature treatment: In zero  |
|             |               | field                                |
+-------------+---------------+--------------------------------------+
| LT-IRM      | Lab Treatment | IRM imparted to specimen prior to    |
|             |               | measurement                          |
+-------------+---------------+--------------------------------------+
| LT-LT-I     | Lab Treatment | Low temperature treatment: In        |
|             |               | laboratory field                     |
+-------------+---------------+--------------------------------------+
| LT-LT-Z     | Lab Treatment | Low temperature treatment: In zero   |
|             |               | field                                |
+-------------+---------------+--------------------------------------+
| LT-M-I      | Lab Treatment | Using microwave radiation: In        |
|             |               | laboratory field                     |
+-------------+---------------+--------------------------------------+
| LT-M-Z      | Lab Treatment | Using microwave radiation: In zero   |
|             |               | field                                |
+-------------+---------------+--------------------------------------+
| LT-NO       | Lab Treatment | No treatments applied before         |
|             |               | measurement                          |
+-------------+---------------+--------------------------------------+
| LT-NRM-APAR | Lab Treatment | Specimen heating and cooling:        |
|             |               | Laboratory                           |
+-------------+---------------+--------------------------------------+
|             |               | field anti-parallel to the NRM       |
|             |               | vector                               |
+-------------+---------------+--------------------------------------+
| LT-NRM-PAR  | Lab Treatment | Specimen heating and cooling:        |
|             |               | Laboratory                           |
+-------------+---------------+--------------------------------------+
|             |               | field parallel to the NRM vector     |
+-------------+---------------+--------------------------------------+
| LT-NRM-PERP | Lab Treatment | Specimen heating and cooling:        |
+-------------+---------------+--------------------------------------+
|             |               | Laboratory field perpendicular to    |
|             |               | the NRM vector                       |
+-------------+---------------+--------------------------------------+
| LT-PTRM-I   | Lab Treatment | pTRM tail check: After zero field    |
|             |               | step,                                |
+-------------+---------------+--------------------------------------+
|             |               | perform an in field cooling          |
+-------------+---------------+--------------------------------------+
| LT-PTRM-MD  | Lab Treatment | pTRM tail check: After in laboratory |
|             |               | field step,                          |
+-------------+---------------+--------------------------------------+
|             |               | perform a zero field cooling at same |
|             |               | temperature                          |
+-------------+---------------+--------------------------------------+
| LT-PTRM-Z   | Lab Treatment | pTRM tail check: After in laboratory |
|             |               | field step,                          |
+-------------+---------------+--------------------------------------+
|             |               | perform a zero field cooling at a    |
|             |               | lower temperature                    |
+-------------+---------------+--------------------------------------+
| LT-T-I      | Lab Treatment | Specimen cooling: In laboratory      |
|             |               | field                                |
+-------------+---------------+--------------------------------------+
| LT-T-Z      | Lab Treatment | Specimen cooling: In zero field      |
+-------------+---------------+--------------------------------------+
| LT-VD       | Lab Treatment | Viscous demagnetization by applying  |
|             |               | MU-metal screening                   |
+-------------+---------------+--------------------------------------+
| LP-X        | Lab Treatment | Susceptibility                       |
+-------------+---------------+--------------------------------------+
| LT-ZF-C     | Lab Treatment | Zero field cooled, low temperature   |
|             |               | IRM imparted                         |
+-------------+---------------+--------------------------------------+
| LT-ZF-CI    | Lab Treatment | Zero field cooled, induced M         |
|             |               | measured on warming                  |
+-------------+---------------+--------------------------------------+
```

## Uploading to MagIC

For uploading to the database, all the individual tables can be
assembled into a single file. Each individual data table is separated
from the next by a series of ‘$>>>>>>>>>>$’ symbols, so a typical
upload file might look like this:

```
tab   locations
location_type   citations   lat_n   lon_e   location    lat_s   lon_w
Drill Site  This study  19.0    156.0   801C    19.0    156.0
Drill Site  This study  19  156 801 19  156
>>>>>>>>>>
tab   samples
citations   lithologies site    sample  geologic_types  geologic_classes
This study   Submarine Basaltic Glass   16r5113 16r5113 Lava Flow   Igneous: Extrusive
This study   Submarine Basaltic Glass   17r1026 17r1026 Lava Flow   Igneous: Extrusive
.
.
.
```

Correctly formatted MagIC data tables can be assembled into a suitable
upload text file by using the program
[upload_magic.py](#upload_magic.py) which reads in all MagIC tables
in a given directory and puts them together as in the above example. You
can invoke [upload_magic.py](#upload_magic.py) on the [command
line](#command_line) or call it within [Pmag GUI](#pmag_gui.py).
[upload_magic.py](#upload_magic.py) creates a contribution file which
can be [uploaded into the MagIC database](#magic_upload). If using
PmagPy to generate your upload file,
[upload_magic.py](#upload_magic.py) has some nifty tricks with
propagating data from one table to another, deleting unneeded columns,
and so on.

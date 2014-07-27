datalinter
==========

datalinter will be a tool to automatically help detect "data smells" -- which, like code smells, are the intuitions of experienced data analysts about when data may be wrong or not accurately reflect what it purports to reflect. datalinter was first discussed and planned at the "Data Smells" session at SRCCON 2014 in Philly. The notes from that session are [here](https://etherpad.mozilla.org/data-smells)

what the hell are you talking about?
------------------------------------

Actual implementation of this tool -- as opposed to proofs of concept -- depends on the creation of the data-smells wiki (or perhaps just Google Spreadsheet) of data-smells.

We're inspired by the [csvlint.rb](https://github.com/theodi/csvlint.rb) project from the Open Data Institute.

There's a tension between a simpler, "dumber" tool that is not type-aware (beyond, maybe, strings and numbers) and a more advanced tool that uses fancy type inference to distinguish different kinds of data to a SQL or better level of precision, e.g. datetimes, lat/longs, probabilities, percentages, addresses or humans' names.

In the case of a simpler tool, output similar to the R `psych` package's describeBy method might be a good example, by highlighting summary statistics so that the user can apply their domain to know if the results make sense. For instance, if the max of a numeric column that the user knows represents latitudes is -3000, the user will be able to know quickly that there's a problem (without the tool having to "know" that there's a problem).
````
> describeBy(dataframe)
            vars   n     mean        sd median trimmed     mad min        max
neighborhood   1 328   164.50     94.83 164.50  164.50  121.57   1     328.00
name           2 328   162.06     93.32 162.50  162.14  119.35   1     323.00
dropoff_cnt    3 328 28562.15 119444.28 792.50 3184.38 1163.10   1 1473849.00
pickup_cnt     4 328 28569.27 129466.72  33.00  811.27   48.93   0 1523726.00
ratio          5 328     0.21      0.32   0.08    0.14    0.10   0       2.27
X              6 327     0.01      0.04   0.00    0.00    0.00   0       0.64
                 range  skew kurtosis      se
neighborhood    327.00  0.00    -1.21    5.24
name           322.00 -0.01    -1.21    5.15
dropoff_cnt 1473848.00  7.48    72.24 6595.21
pickup_cnt  1523726.00  7.05    63.06 7148.60
ratio             2.27  2.57     8.05    0.02
X                 0.64 12.95   184.80    0.00
````

want to help?
-------------
contribute your ideas here in this readme or as an issue! (pull requests welcomed!)

nothing in this README is canonical, so change it or add if you think I/we missed something or are wrong.
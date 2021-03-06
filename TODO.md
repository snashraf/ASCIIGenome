TODO
====

Features
--------

* Allow the user to set the `tmp` directory. By default use a `tmp` other then 
  the system default. On Linux the `tmp` is often pretty small.

* `colorTrack` should allow partial matching of colours with `_` prefix
  equivalent to `light_`. The matching part should be the start of the colour
  name. E.g. `colorTrack _y` same as `colorTrack light_yellow`. Throw error if
  matching is ambiguous.

* Add `-I` flag to `grep` to make it case insensitive.

* Option to log transform quantitative data.

* Implement comments using e.g. // or # 

* Sampling feature: Command to display only a random sample of features in current window. 
  Useful to see the density of features in large intervals with lots of features. E.g.

```
sample INT|percent [track_regex = .*] ...
```

This cmd should operate on the feature set after grep selection. Probably `TrackIntervalFeature.getFeaturesInInterval()` is where
to work for this.

* `export` command to write to file the data in the current interval? API:

```
export [track_regex = .*] > [outdir/]
```

Each track selected by regex will be written to outdir as `chrom_start-end.track_tag.ext` with appropriate `ext`ension.
Coverage and wiggle files will be bedgraph with the score column taken from the Track. Annotation files will bed or gtf
with data taken from the raw. Reference sequence if available will be in fasta format.

* Command to "go to other end" of feature? 

* Add a `nucPrint` command to print nucleotide counts at each position, a bit like pysamstats. API:
`nucPrint INT [INT] [stranded] [pct]`

Refactor
--------

* Test runner `test/run_tests.sh` is effectively not used and clunky. Replace with a *e.g.* snakemake script to run tests properly.

* Populate the enum class `Command` and use `Command.cmdName` in place of the hardcoded command names.

* Each command in CommandHelp should be a class on its own extending CommandHelp. The super class command help
should implement a `validate()` method which is customized to each sub class. `.validate()` should check e.g.
that the command exists, regex are fine, number of args is ok, etc.

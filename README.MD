Usage
=====

```
Usage:
  pcs-tool [<opt> ...]
  Options:
    -f <arg>  --score-file=<arg>       Source score file
    -l        --list                   List score file contents
    -o <arg>  --output=<arg>           Destination score file
    -n <arg>  --match-name=<arg>       Rename match
    -c        --cleanup                Remove entries not related to scores from the match file
    -R <arg>  --reject-division=<arg>
    -A <arg>  --accept-division=<arg>
    -h        --help                   Show help and exit
```

Examples
========

Print divisions and shooters of the score file. If processing flags
are also present in the command line, the output reflects the
_processed_ state of the file. Using `--list` is a good way to test
that your processing command does what you expext it to do.  Once it
does, just replace `--list` with `--output=<scorefile>`.

```
$ psc-tool --score-file=scorefile.psc --list
```

Only purge extra data from the scorefile.

```
$ psc-tool -f scorefile.psc -c -o scorefile-clean.psc
```

Include only PCC divisions, purge data not needed for scoring, change
the competition name, and save to other score file.

```
$ psc-tool --score-file=scorefile.psc --accept-division='/^PCC/' --cleanup --match-name='PCC Mega Match #42' --output=pcc-scorefile.psc
```

Exclude some divisions according to patterns, purge data not needed
for scoring, change the competition name, and save to other score
file. Typically this is done to get the handgun only results. It can
also be done by using --accept-division for each handgun division.

```
$ psc-tool --score-file=scorefile.psc --reject-division='/^PCC/' --reject-division='/^Mini /' --reject-division='/Rifle/' --cleanup --match-name='Pistol Mega Match #42' --output=hg-scorefile.psc

or

$ psc-tool -f scorefile.psc -A Classic -A Open -A Production -A 'Production Optics' -A Revolver -A Standard -c -n 'Pistol Mega Match #42' -o hg-scorefile.psc

```

If command line flag `--list`is used instead if `--output=<scorefile>`
the program prints the file contents as it would be in the processed
file (if processing flags are present).


Author
======

Timo J. Rinne <tri@iki.fi>


License
=======

MIT License


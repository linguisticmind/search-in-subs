# search-in-subs

`search-in-subs` is a Bash script that allows you search for text in SRT subtitle files and gather statistics on the searches it performs.

[![Mindful Technology - search-in-subs: search for text in subtitle files on the command line](https://img.youtube.com/vi/hvcq7WZEIC4/0.jpg)](https://www.youtube.com/watch?v=hvcq7WZEIC4)

## Changelog

<table>
    <tr>
        <th>Version</th>
        <th>Date</th>
        <th>Description</th>
    </tr>
    <tr>
        <td>
            <a href="https://github.com/linguisticmind/search-in-subs/releases/tag/v0.1.1">0.1.1</a>
        </td>
        <td>
           2024-03-20
        </td>
        <td>
            <p>
                Fixed a bug that prevented the last subtitle in the file from getting included in the search.
            </p>
        </td>
    </tr>
</table>

[Read more](CHANGELOG.md)

## Installation

1. Clone this repository to a directory of your choice (e.g. `~/repos`):

    ```bash
    cd ~/repos
    git clone https://github.com/linguisticmind/search-in-subs.git
    ```

2. Symlink or copy the [script file](search-in-subs) to a directory on your `PATH` (e.g. `~/bin`):

    ```bash
    cd ~/bin
    # To symlink:
    ln -sv ../repos/search-in-subs/search-in-subs
    # To copy:
    cp -av ../repos/search-in-subs/search-in-subs .
    ```

3. (OPTIONAL) Symlink or copy the [man page](man/man1/search-in-subs.1) to a directory on your `MANPATH` (e.g. `~/man`):

    ```bash
    cd ~/man/man1 # The `man` directory should contain subdirectories for different manual sections: `man1`, `man2` etc.
    # To symlink:
    ln -sv ../../repos/search-in-subs/man/man1/search-in-subs.1
    # To copy:
    cp -av ../../repos/search-in-subs/man/man1/search-in-subs.1 .
    ```

    A copy of the manual page is also [included in this README file](#manual).

4. (OPTIONAL) Copy the [example config file](config.bash) to the config directory:

    ```bash
    mkdir -v ~/.config/search-in-subs
    cp -v ~/repos/search-in-subs/config.bash ~/.config/search-in-subs
    ```

## Manual

```plain
SEARCH-IN-SUBS(1)           General Commands Manual          SEARCH-IN-SUBS(1)

NAME
       search-in-subs - search for words in subtitle files

SYNOPSIS
        search-in-subs [<options>] -t <search term> ... [<file> ...]

DESCRIPTION
       search-in-subs  allows  the  user  to  search  for text in SRT subtitle
       files.

       At least one search term must be specified to run  a  search  (see  -t,
       --search-term). If no <file> argument is given, a glob pattern set with
       the -g, --default-glob option is used to match subtitle files.

       The built-in value of -g, --default-glob is `*.srt`, which matches  all
       files  with the `.srt` extension in the current working directory. That
       value can be changed to any other glob  pattern  in  the  configuration
       file (see FILES below).

       Shell  options  `nullglob`, `extglob` and `globstar` are enabled inter‐
       nally in search-in-subs, so shell globbing can be used to its full  ca‐
       pacity  when  setting  -g,  --default-glob.  For  example, to match all
       `.srt` files in the current working  directory  recursively,  including
       all  of  its  subdirectories,  one  could  set  -g,  --default-glob  to
       `**/*.srt`.

       search-in-subs can also gather statistics on searches that it runs. Try
       running a search with the -s, --stats option set. For more information,
       see STATISTICS below.

OPTIONS
       -t, --search-term=<search term>
              Text to search for. Can be a fixed string or a  regular  expres‐
              sion depending on the -r, --regex / -R, --no-regex options.

              At least one search term must be given to perform a search. Set‐
              ting this option multiple times sets multiple search terms.

       -g, --default-glob=<glob pattern>
              A shell glob pattern to use when no <file> arguments are  speci‐
              fied. The default is `*.srt`.

              Shell  options  `nullglob`, `extglob` and `globstar` are enabled
              internally in search-in-subs, thus the default glob  pattern  is
              sensitive to those options.

       -v, --verbose
              Print  the  filename even if there were no matches found in that
              file.

       -V, --no-verbose
              Print filenames only for files that had matches. This is the de‐
              fault.

       -i, --inverse
              Only print the names of the files where no matches were found.

       -I, --no-inverse
              Do  not supress printing of matches and names of the files where
              matches were found. This is the default.

       -q, --quiet
              Do not print any matches or filenames. Useful, for  example,  if
              one only wishes to see the statistics or the exit code.

       -Q, --no-quiet
              Do  not  suppress  printing of matches or filenames. This is the
              default.

       -r, --regex
              Use regular expressions instead  of  fixed  strings  in  <search
              term>s.

              Also see REGULAR EXPESSIONS below.

       -R, --no-regex
              Use  fixed  strings  instead  of  regular expressions in <search
              term>s. This is the default.

       -c, --match-case
              Make the search case-sensitive.

       -C, --no-match-case
              Make the search case-insensitive. This is the default.

       -e, --exact-whitespace
              Match whitespace characters exactly as specified in the  <search
              term>.

       -E, --no-exact-whitespace
              Treat  all whitespace characters the same during search - ignor‐
              ing the type of whitespace character, and how many of  them  ap‐
              pear in a sequence. This is the default.

              Whitespace characters are: space, newline, carriage return, hor‐
              izontal tab, vertical tab and form feed (POSIX Extended  Regular
              Expressions `[:space:]` character class).

       -s, --stats
              Show match statistics after search.

              See STATISTICS below for more information.

       -S, --no-stats
              Do not show match statistics after search. This is the default.

       -h, --stats-headers
              Show headers in the statistics table. This is the default.

       -H, --stats-no-headers
              Do not show headers in the statistics table.

       -m, --stats-headers-compact
              Compactify headers in the statistics table.

       -M, --stats-headers-no-compact
              Do  not  compactify headers in the statistics table. This is the
              default.

       -n, --stats-headers-file-numbers
              Show file numbers in the headers of the statistics  table.  This
              is the default.

       -N, --stats-headers-no-file-numbers
              Do not show file numbers in the headers of the statistics table.

       -w, --stats-wrap-filenames
              Wrap filenames in the statistics table. This is the default.

              The  table  always  fits  the  width of the terminal screen, but
              filenames may be printed on multiple lines.

       -W, --stats-no-wrap-filenames
              Do not wrap filenames in the statistics table.

              Files are always printed one per row, regardless of whether  the
              table fits the width of the terminal screen.

       --color
              Colorize the output. This is the default.

       --no-color
              Disable colorization of the output.

       --help Print help.

       --version
              Print version information.

REGULAR EXPRESSIONS
       The  regular expressions used are POSIX Extended Regular Expressions as
       implemented in GNU sed. More information on POSIX  Regular  Expressions
       can     be     found     at     <https://www.gnu.org/software/grep/man‐
       ual/html_node/Regular-Expressions.html>.

STATISTICS
       If the -s, --stats option is enabled, search-in-subs gathers statistics
       on the search that it performs and displays those statistics in a table
       at the end of the output.

       The Matched, Total, Unmatched and Matched % columns of that table  con‐
       tain the following data:

       In the file rows:

       Matched     Number of subtitles in the file that had matches.

       Total       Total number of subtitles in the file.
       Unmatched   Number of subtitles in the file that did not have matches.
       Matched %   Percentage of subtitles in the file that had matches.

       In the Average row:

       Matched     Average number of subtitles per file that had matches.
       Total       Average number of subtitles per file.
       Unmatched   Average number of subtitles per file that did not have matches.
       Matched %   Average percentage of subtitles per file that had matches.

       In the Total row:

       Matched     Total number of subtitles in all files that had matches.
       Total       Total number of subtitles in all files.
       Unmatched   Total number of subtitles in all files that did not have matches.
       Matched %   Total percentage of subtitles in all files that had matches.

       In  the  File  column of the Total row, information is presented in the
       following format:

       <Matched> / <Total> (<Unmatched>) <Matched %>

       Where the <placeholder> values represent the following:

       <Matched>     Total number of files that had matches.
       <Total>       Total number of files.
       <Unmatched>   Total number of files that did not have matches.
       <Matched %>   Percentage of files that had matches.

FILES
       A configuration file can be used to set default options.

       The  configuration  file's  location   is   $XDG_CONFIG_HOME/search-in-
       subs/config.bash. If XDG_CONFIG_HOME is not set, it defaults to ~/.con‐
       fig.

EXIT CODES
       search-in-subs returns the following exit codes:

       0   Success. No errors have occured, and at least one match was found.
       1   An error has occured.
       2   No matches were found (but no errors have occurred). If an error occurs, its exit code takes precedence.

AUTHOR
       Alex Rogers <https://github.com/linguisticmind>

HOMEPAGE
       <https://github.com/linguisticmind/search-in-subs>

COPYRIGHT
       Copyright © 2023 Alex Rogers. License GPLv3+:  GNU  GPL  version  3  or
       later <https://gnu.org/licenses/gpl.html>.

       This  is  free  software:  you  are free to change and redistribute it.
       There is NO WARRANTY, to the extent permitted by law.

SEARCH-IN-SUBS 0.1.1                 2023                    SEARCH-IN-SUBS(1)
```

## License

[GNU General Public License v3.0](LICENSE)

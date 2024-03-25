# search-in-subs

`search-in-subs` is a Bash script that allows you search for text in SRT subtitle files and gather statistics on the searches it performs.

Starting with the version 0.2.0, `search-in-subs` can also play its search results in [`mpv`](https://github.com/mpv-player/mpv).

Video tutorials:

<table>
    <tr>
        <td align='center'>
            <b>v0.2.0</b>: play search results in mpv
        </td>
        <td align='center'>
            <b>v0.1.0</b>: general features overview
        </td>
    </tr>
    <tr>
        <td>
            <a href='https://www.youtube.com/watch?v=M81f6GrqRS4'>
                <img src='https://img.youtube.com/vi/M81f6GrqRS4/0.jpg' alt="Mindful Technology - search-in-subs v0.2.0: play search results in mpv! (SRT subtitles search)" width='360'>
            </a>
        </td>
        <td>
            <a href='https://www.youtube.com/watch?v=hvcq7WZEIC4'>
                <img src='https://img.youtube.com/vi/hvcq7WZEIC4/0.jpg' alt="Mindful Technology - search-in-subs: search for words in subtitle files" width='360'>
            </a>
        </td>
    </tr>
</table>

## Changelog

<table>
    <tr>
        <th>Version</th>
        <th>Date</th>
        <th>Description</th>
    </tr>
    <tr>
        <td>
            <a href="https://github.com/linguisticmind/search-in-subs/releases/tag/v0.2.3">0.2.3</a>
        </td>
        <td>
           2024-03-25
        </td>
        <td>
            <p>
                Now, if a directory is passed as an argument to <code>search-in-subs</code>, files matching the default glob pattern in that directory are added to the search.
            </p>
        </td>
    </tr>
</table>

[Read more](CHANGELOG.md)

## Dependencies

`search-in-subs` requires that [`mpv`](https://mpv.io/), [`ffmpeg`](https://ffmpeg.org/) and [`lua`](https://www.lua.org/) (v5.4) be installed to use [mpv EDL](https://github.com/mpv-player/mpv/blob/master/DOCS/edl-mpv.rst) generation functionality.

On Debian, run `sudo apt install mpv ffmpeg lua5.4` to install these dependencies.

`lua` 5.4 is the version of `lua` that `search-in-subs` was tested with. `search-in-subs` first checks `PATH` for a binary called `lua5.4`, and if that is not available, it uses `lua` as a fallback binary name.

`search-in-subs` was written and tested on Debian 12, and takes advantage of standard utilities that come with the system. In order to run `search-in-subs` on other systems, make sure that the following are installed and available on system's `PATH`:

* Bash >= 5.2.15
* Enhanced getopt
* GNU coreutils
* GNU sed

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
        search-in-subs [<options>] -t <search term> ... [<file|dir> ...]

DESCRIPTION
       search-in-subs  allows  the  user  to  search  for text in SRT subtitle
       files.

       At least one search term must be specified to run  a  search  (see  -t,
       --search-term).  If no <file|dir> argument is given, a glob pattern set
       with the -g, --default-glob option is used to match subtitle files.  If
       a  <file|dir>  argument is a directory, files matching the default glob
       pattern in that directory are added to the search.

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

   mpv EDL generation
       search-in-subs can generate EDL files for  mpv  player,  and  play  the
       search results using it. To use this functionality, mpv, ffmpeg and lua
       (v5.4) must be installed and available on system's PATH.

       In order to generate the EDL files, a video or audio file must exist in
       the  same directory as the subtitle file(s) on which the search is per‐
       formed. The video or audio file must have the same name as the subtitle
       file,  minus the `.srt` extension and potentially a secondary extension
       containing a language code, e.g. `.en.srt`. If  both  video  and  audio
       files  are found, video files take precedence. If multiple video or au‐
       dio files are found, the first one will be chosen for use in the gener‐
       ated EDL files.

       See --edl-* options below for more information.

       More    information    on    mpv   EDL   format   can   be   found   at
       <https://github.com/mpv-player/mpv/blob/master/DOCS/edl-mpv.rst>.

OPTIONS
       Enhanced getopt syntax applies when passing options. There is  one  im‐
       portant  point  to  highlight when it comes to passing options with re‐
       quired vs optional arguments.

       In case of a short option, if an option takes  a  *required*  argument,
       the  argument may be written as a separate parameter, *or* directly af‐
       ter the option character. If an option takes  an  *optional*  argument,
       however, the argument *must* be written directly after the option char‐
       acter.

       In case of a long option, if an option takes a *required* argument, the
       argument  may  be  written as a separate parameter, *or* directly after
       the option name, separated by an equals sign (`=`). If an option  takes
       an  *optional*  argument,  however, the argument *must* be writtent di‐
       rectly after the option name, separated by an equals sign (`=`).

                           Short option   Long option
       Required argument   -o <value>     --option <value>
                           -o<value>      --option=<value>
       Optional argument   -o[<value>]    --option[=<value>]

       Options that take optional arguments can be recognized in  the  options
       list  below  by  their  <value> and the preceding equals sign being en‐
       closed in square brackets:

       -o, --option[=<value>]

   General
       -t, --search-term=<search term>
              Text to search for. Can be a fixed string or a  regular  expres‐
              sion depending on the -r, --regex / -R, --no-regex options.

              At least one search term must be given to perform a search. Set‐
              ting this option multiple times sets multiple search terms.

       -g, --default-glob=<glob pattern>
              A shell glob pattern to use when  no  <file|dir>  arguments  are
              specified, or when a <file|dir> argument is a directory. The de‐
              fault is `*.srt`.

              Shell options `nullglob`, `extglob` and `globstar`  are  enabled
              internally  in  search-in-subs, thus the default glob pattern is
              sensitive to those options.

       -v, --verbose
              Print the filename even if there were no matches found  in  that
              file.

       -V, --no-verbose
              Print filenames only for files that had matches. This is the de‐
              fault.

       -i, --inverse
              Only print the names of the files where no matches were found.

       -I, --no-inverse
              Do not supress printing of matches and names of the files  where
              matches were found. This is the default.

       -q, --quiet
              Do  not  print any matches or filenames. Useful, for example, if
              one only wishes to see the statistics or the exit code.

       -Q, --no-quiet
              Do not suppress printing of matches or filenames.  This  is  the
              default.

       -r, --regex
              Use  regular  expressions  instead  of  fixed strings in <search
              term>s.

              Also see REGULAR EXPESSIONS below.

       -R, --no-regex
              Use fixed strings instead  of  regular  expressions  in  <search
              term>s. This is the default.

       -c, --match-case
              Make the search case-sensitive.

       -C, --no-match-case
              Make the search case-insensitive. This is the default.

       -e, --exact-whitespace
              Match  whitespace characters exactly as specified in the <search
              term>.

       -E, --no-exact-whitespace
              Treat all whitespace characters the same during search -  ignor‐
              ing  the  type of whitespace character, and how many of them ap‐
              pear in a sequence. This is the default.

              Whitespace characters are: space, newline, carriage return, hor‐
              izontal  tab, vertical tab and form feed (POSIX Extended Regular
              Expressions `[:space:]` character class).

   Statistics
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
              Do not compactify headers in the statistics table. This  is  the
              default.

       -n, --stats-headers-file-numbers
              Show  file  numbers in the headers of the statistics table. This
              is the default.

       -N, --stats-headers-no-file-numbers
              Do not show file numbers in the headers of the statistics table.

       -w, --stats-wrap-filenames
              Wrap filenames in the statistics table. This is the default.

              The table always fits the width  of  the  terminal  screen,  but
              filenames may be printed on multiple lines.

       -W, --stats-no-wrap-filenames
              Do not wrap filenames in the statistics table.

              Files  are always printed one per row, regardless of whether the
              table fits the width of the terminal screen.

   mpv EDL generation
       -p, --edl-play
              Play search results in mpv.

              Unless -f, --edl-save-files-relative or -F, --edl-save-files-ab‐
              solute  is  used  together with this option, temporary EDL files
              are generated and saved in the cache directory  (see  FILES  for
              more  information).  The -k, --edl-keep-temporary and -K, --edl-
              no-keep-temporary options control whether or the  temporary  EDL
              files are deleted or kept after mpv player closes.

              If  -f,  --edl-save-files-relative or -F, --edl-save-files-abso‐
              lute is used together with -p, --edl-play, then temporary  files
              are not generated and the saved EDL files are played.

       -P, --edl-no-play
              Do not play search results in mpv. This is the default.

       -k, --edl-play-keep-temporary
              Keep temporary EDL files that are created to play search results
              in mpv.

       -K, --edl-play-no-keep-temporary
              Do not keep temporary EDL files that are created to play  search
              results in mpv. This is the default.

              The temporary files are deleted right after mpv player closes.

       -b, --edl-play-before=<value>
              Add a specified amount of time before each segment when generat‐
              ing EDL files. <value> is in seconds. Precise values with a dec‐
              imal separator are allowed. The default <value> is `0`.

       -a, --edl-play-after=<value>
              Add  a specified amount of time after each segment when generat‐
              ing EDL files. <value> is in seconds. Precise values with a dec‐
              imal separator are allowed. The default <value> is `0`.

       -f,                                              --edl-save-files-rela‐
       tive[={<path>[/]|<path>/<name>.edl|<name>.edl}]
              Save EDL files that use relative paths to refer to source files.
              The default <value> is ``.

              If  <path>  is not given, the EDL files are saved to the current
              working directory. If <name> is not given, the name  `search_re‐
              sults.edl` will be used.

              `.edl`  extension  after <name> is required because it serves to
              distinguish a directory called "<name>" from a name  of  an  EDL
              file.  To save to a directory whose name ends in `.edl` (without
              specifying <name>.edl), add a trailing forward slash (`/`) after
              <path>.

       -F,                                              --edl-save-files-abso‐
       lute[={<path>[/]|<path>/<name>.edl|<name>.edl}]
              Save EDL files that use absolute paths to refer to source files.
              The default <value> is ``.

              See  -f,  --edl-save-files-relative  for information on usage of
              <path> and <name> values.

       --edl-no-save-files
              Do not save EDL files, but  generate  temporary  files  instead.
              This is the default.

              This  option disables -f, --edl-save-files-relative / -F, --edl-
              save-files-absolute.

       -d, --edl-save-mkdir
              Create the EDL save directory (the <path> value  of  --edl-save-
              files-* options) if it does not exist.

       -D, --edl-save-no-mkdir
              Do not create the EDL save directory (the <path> value of --edl-
              save-files-* options) if it does not exist. This is the default.

       -y, --edl-save-overwrite
              Allow overwriting existing files when saving EDL files.

       -Y, --edl-save-no-overwrite
              Allow overwriting existing files when saving EDL files. This  is
              the default.

       -o, --edl-ignore-missing
              Omit  segments  with  missing  videos when generating EDL files.
              This is the default.

              If set, a warning message is shown listing  subtitle  files  for
              which  no  corresponding video file could be identified, but EDL
              files are still generated if at least one  relevant  video  file
              was able to be found.

       -O, --edl-no-ignore-missing
              Do  not  omit  segments  with missing videos when generating EDL
              files.

              If set, an error message is shown  listing  subtitle  files  for
              which  no  corresponding video file could be identified, In this
              case, no EDL files are generated, and search-in-subs exits  with
              exit code `3`.

       -u, --edl-structure=<value>
              Determines  the  structure  of  the  set of generated EDL files.
              <value> can be `flat`,  `subdir`,  `subdir_hidden`,  `subdir_ex‐
              cept_chapters`  or  `subdir_hidden_except_chapters`. The default
              <value> is `flat`.

       --mpv-opts=[:[:]]<opts>
              Options to mpv player.

              <opts> is an option string that follows xargs quoting. It can be
              preceded by a single colon, double colon, or nothing.

              The leading colons control whether <opts> get appended to previ‐
              ously set options, or replace them.

              The phrase 'previously set options' refers to either the default
              value  of  <opts>  set by search-in-subs itself (``), or a value
              set in the configuration file.

              When a single colon (`:`) is used, <opts> replace the previously
              set options.

              When  a  double colon (`::`) is used, <opts> are appended to the
              previously set options.

              When the leading colons are omitted, whether <opts> replace  the
              previously set options, or are appended to them is determined by
              an *additonal* value that is yet again set either by  search-in-
              subs itself (append), or in the configuration file.

   Other
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

       Temporary EDL files that are generated when using  the  -p,  --edl-play
       option are stored in a cache directory.

       The  cache  directory's  location is $XDG_CACHE_HOME/search-in-subs. If
       XDG_CACHE_HOME is not set, it defaults to ~/.cache.

EXIT CODES
       search-in-subs returns the following exit codes:

       0   Success. No errors have occured, and at least one match was found.
       1   A general error has occured.
       2   No matches were found.
       3   EDL generation failed. Can only occur if -O, --edl-no-ignore-missing is set.

AUTHOR
       Alex Rogers <https://github.com/linguisticmind>

HOMEPAGE
       <https://github.com/linguisticmind/search-in-subs>

COPYRIGHT
       Copyright © 2023 Alex Rogers. License GPLv3+:  GNU  GPL  version  3  or
       later <https://gnu.org/licenses/gpl.html>.

       This  is  free  software:  you  are free to change and redistribute it.
       There is NO WARRANTY, to the extent permitted by law.

SEARCH-IN-SUBS 0.2.2                 2024                    SEARCH-IN-SUBS(1)
```

## License

[GNU General Public License v3.0](LICENSE)

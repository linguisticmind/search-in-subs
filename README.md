# search-in-subs

`search-in-subs` is a Bash script that allows you to search for text in SRT subtitle files and gather statistics on the searches it performs.

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
                <img src='https://img.youtube.com/vi/M81f6GrqRS4/0.jpg' alt='Mindful Technology - search-in-subs v0.2.0: play search results in mpv! (SRT subtitles search)' width='360'>
            </a>
        </td>
        <td>
            <a href='https://www.youtube.com/watch?v=hvcq7WZEIC4'>
                <img src='https://img.youtube.com/vi/hvcq7WZEIC4/0.jpg' alt='Mindful Technology - search-in-subs: search for words in subtitle files' width='360'>
            </a>
        </td>
    </tr>
</table>

<a href='https://ko-fi.com/linguisticmind'><img src='https://github.com/linguisticmind/linguisticmind/raw/master/res/kofi/kofi_donate_1.svg' alt='Support me on Ko-fi' height='48'></a>

## Changelog

<table>
    <tr>
        <th>Version</th>
        <th>Date</th>
        <th>Description</th>
    </tr>
    <tr>
        <td>
            <a href='https://github.com/linguisticmind/search-in-subs/releases/tag/v0.3.4'>0.3.4</a>
        </td>
        <td>
           2025-03-25
        </td>
        <td>
            <p>
                Bug fix: Last word of a subtitle file wasn't matching properly. Now it does.
            </p>
            <p>
                <code>conf_chapter_title</code>: Renamed <code>%{text_raw}</code> to <code>%{text_tall}</code> since that string has formatting tags stripped.
            </p>
        </td>
    </tr>
    <tr>
        <td>
            <a href='https://github.com/linguisticmind/search-in-subs/releases/tag/v0.3.3'>0.3.3</a>
        </td>
        <td>
           2025-03-25
        </td>
        <td>
            <p>
                Removed <code>conf_srt_secondary_ext</code> and <code>--edl-play-srt-secondary-ext</code> in favor of a general algorithm for finding video files corresponding to subtitle files. There is no need to define custom secondary extensions anymore. Any number of additional extensions with any contents is supported. Improving the fix of <a href='https://github.com/linguisticmind/search-in-subs/issues/4'>#4</a>.
            </p>
        </td>
    </tr>
    <tr>
        <td>
            <a href='https://github.com/linguisticmind/search-in-subs/releases/tag/v0.3.2'>0.3.2</a>
        </td>
        <td>
           2025-03-25
        </td>
        <td>
            <p>
                Added <code>conf_chapter_title</code>. This setting lets you customize chapter titles in generated mpv EDL files. Idea from discussion <a href='https://github.com/linguisticmind/search-in-subs/discussions/8'>#8</a>.
            </p>
        </td>
    </tr>
    <tr>
        <td>
            <a href='https://github.com/linguisticmind/search-in-subs/releases/tag/v0.3.1'>0.3.1</a>
        </td>
        <td>
           2025-03-24
        </td>
        <td>
            <p>
                Added <code>-j, --filenames-only</code>, <code>-J, --no-filenames-only</code>. This option suppresses printing of matches, only printing the names of the files where matches were found.
            </p>
        </td>
    </tr>
    <tr>
        <td>
            <a href='https://github.com/linguisticmind/search-in-subs/releases/tag/v0.3.0'>0.3.0</a>
        </td>
        <td>
            2025-03-23
        </td>
        <td>
            <p>
                <p>
                    <strong>We are at 0.3.0!</strong>
                </p>
                <ul>
                    <li>The new <code>--config</code> option makes configuring <code>search-in-subs</code> more convenient by adding the ability to generate a configuration file and open it for editing.</li>
                    <li><code>-f, --edl-save-files-relative</code>, <code>-F, --edl-save-files-absolute</code>, <code>--edl-no-save-files</code> were reorganized as <code>-f, --edl-save</code>, <code>-F, --edl-no-save</code>, and <code>--edl-save-paths</code>.</li>
                    <li><code>--color</code> now takes an optional argument with the value of <code>'always'</code>, <code>'auto'</code>, or <code>'never'</code>. In the <code>'auto'</code> mode, colorization is applied only if stdout of <code>search-in-subs</code> is connected to a terminal.</li>
                    <li><code>--help</code> now opens the man page.</li>
                    <li>Various improvements to the man mage were made, including the addition of a new <code>CONFIGURATION</code> section.</li>
                    <li>
                        <p>
                            Introducing <i>configuration file-only parameters</i>. These are settings that can only be set in the configuration file, and don't have a command-line counterpart.
                        </p>
                        <ul>
                            <li>The default name of a generated EDL file is now configurable: <code>conf_edl_default_name</code>.
                            <li><del>It is now possible to set custom secondary filename extensions for SRT files to allow <code>search-in-subs</code> to correctly match up unusually-named subtitle files with their video counterparts: <code>conf_srt_secondary_ext</code>. Also added <code>--edl-play-srt-secondary-ext</code> for setting a secondary filename extension temporarily on the command line. Fixes <a href='https://github.com/linguisticmind/search-in-subs/issues/4'>#4</a>.</del> See v0.3.3.</li>
                            <li>The default glob setting has been made configuration file-only since its command-line counterpart didn't really have any use. The new variable name is <code>conf_default_glob</code>.</li>
                        </ul>
                    </li>
                </ul>
            </p>
            <hr>
            <p>
                <b>ATTENTION</b>: This release introduces <strong>breaking changes</strong>. It is recommended that you back up your configuration file, generate a new one, and manually copy over your settings from the backup file into the newly-generated configuration file.
            </p>
            <dl>
                <dt>
                    What does <code>search-in-subs</code> do when it generates a configuration file?
                </dt>
                <dd>
                    It takes the part of <a href='search-in-subs'>its own source code</a> demarcated by lines <code># --- BEGIN config ---</code> and <code># --- END config ---</code>, comments out non-empty lines from that part, and saves the resulting text to <code>~/.config/search-in-subs/config.bash</code>. See the <a href='https://github.com/linguisticmind/search-in-subs#manual'>man page</a> for more information about the functionality provided by the new <code>--config</code> option.
                </dd>
            </dl>
            <p>
                The suggested procedure for migrating your settings is:
            </p>
            <div>
            <pre>cd ~/.config/search-in-subs
mv -nv config.bash config.bash.bak
search-in-subs --config</pre>
            </div>
            <p>
                <code>search-in-subs</code> will generate a new configuration file and ask if you would like to open it in a text editor. Reply <code>y</code> or simply press Enter.
            </p>
            <p>
                Open <code>~/.config/search-in-subs/config.bash.bak</code> in a text editor as well. If you're using <code>vim</code>, you can run <code>:tabnew ~/.config/search-in-subs/config.bash.bak</code>.
            </p>
            <p>
                Then copy your settings over to the new configuration file. It should be clear from just looking at the file what goes where.
            </p>
            <p>
                If you run into problems, please <a href='https://github.com/linguisticmind/search-in-subs/issues'>open an issue</a> or <a href='https://github.com/linguisticmind/search-in-subs/discussions'>ask a question</a>.
            </p>
        </td>
    </tr>
</table>

[Read more](CHANGELOG.md)

## Dependencies

`search-in-subs` requires that [`mpv`](https://mpv.io/), [`ffmpeg`](https://ffmpeg.org/) and [`lua`](https://www.lua.org/) (v5.4) be installed to use [mpv EDL](https://github.com/mpv-player/mpv/blob/master/DOCS/edl-mpv.rst) generation functionality.

On Debian, run `sudo apt install mpv ffmpeg lua5.4` to install these dependencies.

`lua` 5.4 is the version of `lua` that `search-in-subs` was tested with. `search-in-subs` first checks `PATH` for a binary called `lua5.4`, and if that is not available, it uses `lua` as a fallback binary name.

If [`bat`](https://github.com/sharkdp/bat) is installed, it will be used to pretty-print the preview of a generated configuration file when using `--config`.

On Debian, run `sudo apt install bat` to install it.

Note that on Debian, `bat`'s executable is [called `batcat` instead of `bat`](https://github.com/sharkdp/bat/issues/982).

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

## Manual

```plain
SEARCH-IN-SUBS(1)           General Commands Manual          SEARCH-IN-SUBS(1)

NAME
       search-in-subs - search for words in subtitle files

SYNOPSIS
       search-in-subs [<options>] -t <search_term> ... [<file|dir> ...]

DESCRIPTION
       search-in-subs  allows  the  user  to  search  for text in SRT subtitle
       files.

       At least one search term  must  be  specified  to  run  a  search  (see
       -t, --search-term).  If no <file|dir> argument is given, a glob pattern
       set with the conf_default_glob option is used to match subtitle  files.
       If  a  <file|dir>  argument  is a directory, files matching the default
       glob pattern in that directory are added to the search.

       The default value of conf_default_glob is '*.srt',  which  matches  all
       files  with the '.srt' extension in the current working directory. That
       value can be changed to any other glob  pattern  in  the  configuration
       file (see CONFIGURATION and FILES below).

       Shell  options  'nullglob', 'extglob' and 'globstar' are enabled inter‐
       nally in search-in-subs, so shell globbing can be used to its full  ca‐
       pacity when setting conf_default_glob. For example, to match all '.srt'
       files in the current working directory recursively,  including  all  of
       its subdirectories, one could set conf_default_glob to '**/*.srt'.

       search-in-subs can also gather statistics on searches that it runs. Try
       running a search with the -s, --stats option set. For more information,
       see STATISTICS below.

   mpv EDL generation
       search-in-subs  can  generate  EDL  files  for mpv player, and play the
       search results using it. To use this  functionality,  mpv,  ffmpeg  and
       lua (v5.4) must be installed and available on system's PATH.

       In order to generate the EDL files, a video or audio file must exist in
       the same directory as the subtitle file(s) on which the search is  per‐
       formed. The video or audio file must have the same name as the subtitle
       file, minus the '.srt' extension, and potentially additional extensions
       containing  language  codes  or  other information, e.g. '.en.srt'. Any
       number of additional extensions is allowed. If  both  video  and  audio
       files  are found, video files take precedence. If multiple video or au‐
       dio files are found, the first one will be chosen for use in the gener‐
       ated EDL files.

       See --edl-* options below for more information.

       More information on mpv EDL format can be found at <https://github.com/
       mpv-player/mpv/blob/master/DOCS/edl-mpv.rst>.

OPTIONS
   Passing arguments to options
       Enhanced getopt syntax applies when passing options. There is  one  im‐
       portant  point  to  highlight when it comes to passing options with re‐
       quired vs optional arguments.

       In case of a short option, if an option takes a required argument,  the
       argument  may be written as a separate parameter, or directly after the
       option character. If an option takes an optional argument, however, the
       argument must be written directly after the option character.

       In  case  of a long option, if an option takes a required argument, the
       argument may be written as a separate parameter, or directly after  the
       option  name,  separated by an equals sign ('='). If an option takes an
       optional argument, however, the argument must be written directly after
       the option name, separated by an equals sign ('=').

                           Short option   Long option
       Required argument   -o <value>     --option <value>
                           -o<value>      --option=<value>
       Optional argument   -o[<value>]    --option[=<value>]

       Options  that  take optional arguments can be recognized in the options
       list below by their <value> and the preceding  equals  sign  being  en‐
       closed in square brackets:

       -o, --option[=<value>]

   General
       -t, --search-term=<search_term>
              Text  to  search for. Can be a fixed string or a regular expres‐
              sion depending on the -r, --regex / -R, --no-regex options.

              At least one search term must be given to perform a search. Set‐
              ting this option multiple times sets multiple search terms.

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

       -j, --filenames-only
              Suppress printing of matched subtitles. Only print the  name  of
              the file where matches were found.

       -J, --no-filenames-only
              Do  not  supress  printing of matched subtitles. This is the de‐
              fault.

       -q, --quiet
              Do not print any matches or filenames. Useful, for  example,  if
              one only wishes to see the statistics or the exit status.

       -Q, --no-quiet
              Do  not  suppress  printing of matches or filenames. This is the
              default.

       -r, --regex
              Use  regular   expressions   instead   of   fixed   strings   in
              <search_term>s.

              The  regular expressions used are POSIX Extended Regular Expres‐
              sions as implemented in GNU sed.  More  information  on  can  be
              found        at        <https://www.gnu.org/software/sed/manual/
              sed.html#sed-regular-expressions>.

       -R, --no-regex
              Use  fixed   strings   instead   of   regular   expressions   in
              <search_term>s. This is the default.

       -c, --match-case
              Make the search case-sensitive.

       -C, --no-match-case
              Make the search case-insensitive. This is the default.

       -e, --exact-whitespace
              Match   whitespace   characters  exactly  as  specified  in  the
              <search_term>.

       -E, --no-exact-whitespace
              Treat all whitespace characters the same during search -  ignor‐
              ing  the  type of whitespace character, and how many of them ap‐
              pear in a sequence. This is the default.

              Whitespace characters are: space, newline, carriage return, hor‐
              izontal  tab, vertical tab and form feed (POSIX Extended Regular
              Expressions '[:space:]' character class).

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

              Unless             -f, --edl-save-files-relative              or
              -F, --edl-save-files-absolute is used together with this option,
              temporary EDL files are generated and saved in the cache  direc‐
              tory     (see     FILES     for     more    information).    The
              -k, --edl-keep-temporary and -K, --edl-no-keep-temporary options
              control  whether  or the temporary EDL files are deleted or kept
              after mpv player closes.

              If               -f, --edl-save-files-relative                or
              -F, --edl-save-files-absolute     is    used    together    with
              -p, --edl-play, then temporary files are not generated  and  the
              saved EDL files are played.

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
              imal separator are allowed. The default <value> is 0.

       -a, --edl-play-after=<value>
              Add  a specified amount of time after each segment when generat‐
              ing EDL files. <value> is in seconds. Precise values with a dec‐
              imal separator are allowed. The default <value> is 0.

       -f, --edl-save[={<path>[/]|<path>/<name>.edl|<name>.edl}]
              Save  EDL  files  to  a specified location instead of generating
              temporary ones.

              If <path> is not given, the EDL files are saved to  the  current
              working  directory.  If  <name>  is  not  given, the name set by
              conf_edl_default_name will be used.

              A '.edl' extension after <name> is required because it serves to
              distinguish  a  directory  called "<name>" from a name of an EDL
              file. To save to a directory whose name ends in '.edl'  (without
              specifying "<name>.edl"), add a trailing forward slash ('/') af‐
              ter <path>.

       -F, --edl-no-save
              Do not save EDL files, but  generate  temporary  files  instead.
              This is the default.

       --edl-save-paths=<value>
              What  kind of paths to use in saved EDL files to refer to source
              files.

              relative
                     Use relative paths. This is the default.

              absolute
                     Use absolute paths.

       -d, --edl-save-mkdir
              Create  the  EDL   save   directory   (the   <path>   value   of
              --edl-save-files-* options) if it does not exist.

       -D, --edl-save-no-mkdir
              Do  not  create  the  EDL  save  directory  (the <path> value of
              --edl-save-files-* options) if it does not exist.  This  is  the
              default.

       -y, --edl-save-overwrite
              Allow overwriting existing files when saving EDL files.

       -Y, --edl-save-no-overwrite
              Do  not  allow overwriting existing files when saving EDL files.
              This is the default.

       -o, --edl-ignore-missing
              Omit segments with missing videos  when  generating  EDL  files.
              This is the default.

              If  set,  a  warning message is shown listing subtitle files for
              which no corresponding video file could be identified,  but  EDL
              files  are  still  generated if at least one relevant video file
              was able to be found.

       -O, --edl-no-ignore-missing
              Do not omit segments with missing  videos  when  generating  EDL
              files.

              If  set,  an  error  message is shown listing subtitle files for
              which no corresponding video file could be identified,  In  this
              case,  no EDL files are generated, and search-in-subs exits with
              exit status 3.

       -u, --edl-structure=<value>
              Determines the structure of the  set  of  generated  EDL  files.
              <value>    can    be    'flat',    'subdir',    'subdir_hidden',
              'subdir_except_chapters' or 'subdir_hidden_except_chapters'. The
              default <value> is 'flat'.

       --mpv-opts=[:[:]]<opts>
              Options to mpv player.

              <opts> is an option string that follows xargs quoting. It can be
              preceded by a single colon, double colon, or nothing.

              The leading colons control whether <opts> get appended to previ‐
              ously set options, or replace them.

              The phrase 'previously set options' refers to either the default
              value of <opts> set by search-in-subs itself (''),  or  a  value
              set in the configuration file.

              When a single colon (':') is used, <opts> replace the previously
              set options.

              When a double colon ('::') is used, <opts> are appended  to  the
              previously set options.

              When  the leading colons are omitted, whether <opts> replace the
              previously set options, or are appended to them is determined by
              an  *additonal* value that is yet again set either by search-in-
              subs itself (append), or in the configuration file.

              The name of the variable that controls this  has  the  following
              format:  optdata__<opt_name>__<optdata_name> where <opt_name> is
              the name of the option, and <optdata_name> is the  name  of  the
              piece  of  option  data  that  the  variable holds. In this case
              <optdata_name> is 'append'.  So  if  the  option's  variable  is
              called  opt_mpv_opts,  then the variable that controls what hap‐
              pens  when  the   leading   colons   are   omitted   is   called
              optdata__mpv_opts__append.

   Other
       --color[={always|auto|never}]
              Colorize the output. The default value is 'auto'.

              always    Always colorize.

              [auto]    Colorize if stdout is connected to a terminal.

              never     Never colorize.

       --no-color
              Disable  colorization  of  the output. Equivalent to -c, --color
              set to 'never'.

       --help Open the man page.

       --version
              Print version information.

       --config[={edit|generate|remove|auto}]
              Perform an action on the configuration file. See also CONFIGURA‐
              TION and FILES below.

              edit   Open an existing configuration file in a text editor.

              generate
                     Generate a new configuration file.

              remove Delete  an existing configuration file. If the configura‐
                     tion directory doesn't have any other files, it  is  also
                     deleted.

              [auto] Generate a configuration file if it does not exist. If it
                     does, open it in a text editor. This is the default.

CONFIGURATION
       This is how command line options and configuration variables correspond
       to each other. The command line option on the left sets the variable(s)
       on the right internally.

       Special symbols in the right column:

       -      This option is non-configurable.

       "      This option sets the same variable(s) as the one above.

       -t, --search-term=<value>             opt_search_term
       -v, --verbose                         opt_verbose
       -V, --no-verbose                      "
       -i, --inverse                         opt_inverse
       -I, --no-inverse                      "
       -j, --filenames-only                  opt_filenames_only
       -J, --no-filenames-only               "
       -q, --quiet                           opt_quiet
       -Q, --no-quiet                        "
       -r, --regex                           opt_regex
       -R, --no-regex                        "
       -c, --match-case                      opt_match_case
       -C, --no-match-case                   "
       -e, --exact-whitespace                opt_exact_whitespace
       -E, --no-exact-whitespace             "
       -s, --stats                           opt_stats
       -S, --no-stats                        "
       -h, --stats-headers                   opt_stats_headers
       -H, --stats-no-headers                "
       -m, --stats-headers-compact           opt_stats_headers_compact
       -M, --stats-headers-no-compact        "
       -n, --stats-headers-file-numbers      opt_stats_headers_file_numbers
       -N, --stats-headers-no-file-numbers   "
       -w, --stats-wrap-filenames            opt_stats_wrap_filenames
       -W, --stats-no-wrap-filenames         "
       -p, --edl-play                        opt_edl_play
       -P, --edl-no-play                     "
       -k, --edl-play-keep-temporary         opt_edl_play_keep_temporary
       -K, --edl-play-no-keep-temporary      "
       -b, --edl-play-before=<value>         opt_edl_play_before
       -a, --edl-play-after=<value>          opt_edl_play_after
       -f, --edl-save[=<value>]              opt_edl_save
                                             optdata__edl_save__file
       -F, --edl-no-save                     "
       --edl-save-paths=<value>              opt_edl_save_paths
       -d, --edl-save-mkdir                  opt_edl_save_mkdir
       -D, --edl-save-no-mkdir               "
       -y, --edl-save-overwrite              opt_edl_save_overwrite
       -Y, --edl-save-no-overwrite           "
       -o, --edl-ignore-missing              opt_edl_ignore_missing
       -O, --edl-no-ignore-missing           "
       -u, --edl-structure=<value>           opt_edl_structure
       --mpv-opts=<value>                    opt_mpv_opts
                                             optdata__mpv_opts__append
       --color[=<value>]                     opt_color
       --no-color                            "
       --help                                -
       --version                             -
       --config[=<value>]                    -

   Configuration file-only parameters
       conf_default_glob
              A shell glob pattern to use when  no  <file|dir>  arguments  are
              specified, or when a <file|dir> argument is a directory. The de‐
              fault is '*.srt'.

              Shell options 'nullglob', 'extglob' and 'globstar'  are  enabled
              internally  in  search-in-subs, thus the default glob pattern is
              sensitive to those options.

       conf_edl_default_name
              The default name for a generated EDL file. The default value  is
              'search_results'.

       conf_chapter_title
              A  generated  EDL's  chapter  title.  The value is a string with
              placeholders. See also PLACEHOLDER FORMAT.

              If set to an empty string (''), the result is equivalent to  us‐
              ing  the  value of '%{text_abbr}', but with a slight performance
              increase. The default value is ''.

              The following placeholders are supported:

              %{file_base}
                     Base name of the video file.

              %{file_edl}
                     Path to the video file as it  appears  in  the  generated
                     EDL.

              %{file_rel}
                     Path  to  the  video file relative to the current working
                     directory.

              %{file_abs}
                     Absolute path to the video file.

              %{n}   Subtitle number as it appears in the SRT file.

              %{timecodes_raw}
                     Timecodes as they appear in the SRT file.

              %{timecode_start}
                     Opening timecode in the mpv format.

              %{timecode_start_raw}
                     Opening timecode as it appears in the SRT file.

              %{timecode_end}
                     Closing timecode in the mpv format.

              %{timecode_end_raw}
                     Closing timecode as it appears in the SRT file.

              %{text_tall}
                     Subtitle text as it appears in the SRT  file.  Formatting
                     tags such as <i></i> are removed.

              %{text_long}
                     Like  %{text_tall},  but with newlines replaced with spa‐
                     ces.

              %{text_abbr}
                     Like %{text_tall}, but only showing the first line of the
                     subtitle.

EXIT STATUS
       0      Success.  No  errors  have  occured,  and at least one match was
              found.

       1      A general error has occured.

       2      No matches were found.

       3      EDL     generation     failed.     Can     only     occur     if
              -O, --edl-no-ignore-missing is set.

ENVIRONMENT
       The  values  of  VISUAL  and EDITOR environment variables determine the
       text editor when opening configuration files with --config.

       VISUAL is evaluated first. If that is not set, then  EDITOR  is  evalu‐
       ated. If neither is set, nano is used as the text editor.

FILES
       A  configuration  file  can  be  used to change the default behavior of
       search-in-subs.

       The configuration file's location is  "$XDG_CONFIG_HOME/search-in-subs/
       config.bash".  If  "XDG_CONFIG_HOME" is not set, it defaults to "$HOME/
       .config".

       Temporary EDL files that are generated when  using  the  -p, --edl-play
       option are stored in a cache directory.

       The  cache directory's location is "$XDG_CACHE_HOME/search-in-subs". If
       "XDG_CACHE_HOME" is not set, it defaults to "$HOME/.cache".

STATISTICS
       If the -s, --stats option is enabled, search-in-subs gathers statistics
       on the search that it performs and displays those statistics in a table
       at the end of the output.

       The 'Matched', 'Total', 'Unmatched' and 'Matched %' columns of that ta‐
       ble contain the following data:

       In the file rows:

       Matched     Number of subtitles in the file that had matches.
       Total       Total number of subtitles in the file.
       Unmatched   Number of subtitles in the file that did not have matches.
       Matched %   Percentage of subtitles in the file that had matches.

       In the 'Average' row:

       Matched     Average number of subtitles per file that had matches.
       Total       Average number of subtitles per file.
       Unmatched   Average number of subtitles per file that did not have matches.

       Matched %   Average percentage of subtitles per file that had matches.

       In the 'Total' row:

       Matched     Total number of subtitles in all files that had matches.
       Total       Total number of subtitles in all files.
       Unmatched   Total number of subtitles in all files that did not have matches.
       Matched %   Total percentage of subtitles in all files that had matches.

       In  the  'File'  column of the 'Total' row, information is presented in
       the following format:

       <Matched> / <Total> (<Unmatched>) <Matched %>

       Where the placeholder values represent the following:

       <Matched>     Total number of files that had matches.
       <Total>       Total number of files.
       <Unmatched>   Total number of files that did not have matches.
       <Matched %>   Percentage of files that had matches.

PLACEHOLDER FORMAT
       (1)    %<name>

              or

       (2)    %{<name>:-<fallback>:+<override>}

              :-<fallback> and :+<override> are optional and may go in any or‐
              der.

       <name> is a placeholder name.

       <fallback>  and <override> are also strings with placeholders just like
       the entire string.

       <fallback> is substituted if the replacement value is unavailable.

       <override> is substituted instead of the replacement value allowing to,
       for     instance,    insert    extra    characters    next    to    it:
       '%{date:+%{date}_}%{name}.mp4'.

       In strings with placeholders, '\', '%', '{', ':', and '}'  are  special
       characters.  They  can  be  escaped with backslashes ('\') to represent
       their literal values.

AUTHOR
       Alex Rogers <https://github.com/linguisticmind>

HOMEPAGE
       <https://github.com/linguisticmind/dechapter>

AUTHOR
       Alex Rogers <https://github.com/linguisticmind>

HOMEPAGE
       <https://github.com/linguisticmind/search-in-subs>

COPYRIGHT
       Copyright © 2025 Alex Rogers. License GPLv3+:  GNU  GPL  version  3  or
       later <https://gnu.org/licenses/gpl.html>.

       This  is  free  software:  you  are free to change and redistribute it.
       There is NO WARRANTY, to the extent permitted by law.

SEARCH-IN-SUBS 0.3.4              2025-03-25                 SEARCH-IN-SUBS(1)
```

## License

[GNU General Public License v3.0](LICENSE)

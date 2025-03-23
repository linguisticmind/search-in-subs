# search-in-subs changelog

<table>
    <tr>
        <th>Version</th>
        <th>Date</th>
        <th>Description</th>
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
                            <li>It is now possible to set custom secondary filename extensions for SRT files to allow <code>search-in-subs</code> to correctly match up unusually-named subtitle files with their video counterparts: <code>conf_srt_secondary_ext</code>. Also added <code>--edl-play-srt-secondary-ext</code> for setting a secondary filename extension temporarily on the command line. Fixes <a href='https://github.com/linguisticmind/search-in-subs/issues/4'>#4</a>.</li>
                            <li>
                                The default glob setting has been made configuration file-only since its command-line counterpart didn't really have any use. The new variable name is <code>conf_default_glob</code>.
                            </li>
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
    <tr>
        <td>
            <a href='https://github.com/linguisticmind/search-in-subs/releases/tag/v0.2.6'>0.2.6</a>
        </td>
        <td>
            2025-03-22
        </td>
        <td>
            <p>
                Standardization fixes:
                <ul>
                    <li>
                        Code:
                        <ul>
                            <li>
                                <p>
                                    <b>BREAKING</b>: Shifted to a new naming convention for variables that hold additional data related to options. The new format for the names of such variables is <code>optdata&lowbar;&lowbar;&lt;opt_name&gt;&lowbar;&lowbar;&lt;optdata_name&gt;</code> where <code>&lt;opt_name&gt;</code> is the name of the option, and <code>&lt;optdata_name&gt;</code> is the name of the piece of option data that the variable holds. Note the double underscore (<code>&lowbar;&lowbar;</code>) surrounding the <code>&lt;opt_name&gt;</code>.
                                </p>
                                <p>
                                    This prevents conflating the main option variables (<code>opt_&lt;opt_name&gt;</code>) with the variables that hold additional option data, and allows for easy access to variables from either set via the <code>${!prefix&ast;}</code> and <code>${!prefix@}</code> <a href='https://www.gnu.org/software/bash/manual/bash.html#Shell-Parameter-Expansion'>parameter expansions</a>.
                                </p>
                            </li>
                            <li>Shifted to using a <code>script_name</code> variable set to <code>"${BASH_SOURCE##*/}"</code> to hold the name of the script shown in messages. Prior to this, <code>"${BASH_SOURCE##*/}"</code> was used directly everywhere.</li>
                            <li>Shifted to using a more semantically clear <code>==</code> comparison operator instead of <code>=</code> in conditional statements. This ensures consistency with comparison operators in other programming languages, and in <a href='https://www.gnu.org/software/bash/manual/bash.html#Shell-Arithmetic'>Bash's own arithmetic expressions</a>.</li>
                        </ul>
                    </li>
                    <li>man page: renamed the <code>exit codes</code> section to <code>exit status</code>, removed superfluous text from it, and moved it after the <code>options</code> section.</li>
                </ul>
            </p>
            <p>man page: fixed a typo</p>
        </td>
    </tr>
    <tr>
        <td>
            <a href='https://github.com/linguisticmind/search-in-subs/releases/tag/v0.2.5'>0.2.5</a>
        </td>
        <td>
           2024-07-18
        </td>
        <td>
            <p>
                <b>IMPORTANT</b>: Updated the <code>re_esc</code> function which previously did not escape backslashes (<code>&bsol;</code>) for use in regular expressions. This would lead to incorrect handling of search terms containing backslashes.
            </p>
            <p>
                Minor stylistic and formatting updates to README, man page, and the main script.
            </p>
        </td>
    </tr>
    <tr>
        <td>
            <a href='https://github.com/linguisticmind/search-in-subs/releases/tag/v0.2.4'>0.2.4</a>
        </td>
        <td>
           2024-05-25
        </td>
        <td>
            <p>
                Improved the method of quoting strings for displaying them in messages:
                <ul>
                    <li>All instances of using <code>\'"${parameter//\'/\'\\\'\'}"\'</code> were replaced with <code>"${parameter@Q}"</code>.</li>
                    <li>All instances of using <code>ls -1d "${array[@]}"</code> were replaced with <code>printf '%s\n' "${array[@]@Q}"</code>.</li>
                </ul>
            </p>
            <p>
                Improved handling of removal of trailing forward slashes when passing the <code>&lt;path&gt;[/]</code> value to <code>-f, --edl-save-files-relative</code> and <code>-F, --edl-save-files-absolute</code>, and when passing a directory as a non-option argument:
                <ul>
                    <li>Now, not one, but all trailing forward slashes are removed.</li>
                    <li>If the path consists of forward slashes only (one or more of them), a single forward slash representing the root directory is kept.</li>
                </ul>
            </p>
            <p>
                Improved formatting of the built-in help message.<br>
                Improved phrasing regarding the default value of <code>-f, --edl-save-files-relative</code> and <code>-F, --edl-save-files-absolute</code> in the man page.<br>
                Fixed further inaccuracies and formatting shortcomings in the script's built-in help message, the man page, the README, and the CHANGELOG files.
            </p>
            <p>
                Removed a superfluous <code>IFS=' '</code> from the <code>getopt</code> line.
            </p>
        </td>
    </tr>
    <tr>
        <td>
            <a href='https://github.com/linguisticmind/search-in-subs/releases/tag/v0.2.3'>0.2.3</a>
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
    <tr>
        <td>
            <a href='https://github.com/linguisticmind/search-in-subs/releases/tag/v0.2.2'>0.2.2</a>
        </td>
        <td>
           2024-03-22
        </td>
        <td>
            <p>
                Improved <code>lua</code> binary identification. <code>lua5.4</code> is now preferred, <code>lua</code> becoming a fallback.
            </p>
        </td>
    </tr>
    <tr>
        <td>
            <a href='https://github.com/linguisticmind/search-in-subs/releases/tag/v0.2.1'>0.2.1</a>
        </td>
        <td>
           2024-03-21
        </td>
        <td>
            <p>
                Added <code>--edl-no-save-files</code>.
            </p>
            <p>
                Fixed a bug where <code>search-in-subs</code> attempted to clear cache while using an <code>--edl-save-files-&ast;</code> option. This also resulted in an erroneous exit code.
            </p>
        </td>
    </tr>
    <tr>
        <td>
            <a href='https://github.com/linguisticmind/search-in-subs/releases/tag/v0.2.0'>0.2.0</a>
        </td>
        <td>
           2024-03-20 
        </td>
        <td>
            <p>
                Added mpv integration.
            </p>
        </td>
    </tr>
    <tr>
        <td>
            <a href='https://github.com/linguisticmind/search-in-subs/releases/tag/v0.1.1'>0.1.1</a>
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
    <tr>
        <td>
            <a href='https://github.com/linguisticmind/search-in-subs/releases/tag/v0.1.0'>0.1.0</a></td>
        <td>
            2024-02-08
        </td>
        <td>
            <p>
                Initial release.
            </p>
        </td>
    </tr>
</table>

# search-in-subs changelog

<table>
    <tr>
        <th>Version</th>
        <th>Date</th>
        <th>Description</th>
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
                            <li>Shifted to using a <code>script_name</code> variable set to <code>"${BASH_SOURCE##*/}"</code> to hold the name of the script shown in messages. Prior to this, <code>"${BASH_SOURCE##*/}"</code> was used directly everywhere.</li>
                            <li>Shifted to using a more semantically clear <code>==</code> comparison operator instead of <code>=</code> in conditional statements. This ensures consistency with comparison operators in other programming languages, and in <a href='https://www.gnu.org/software/bash/manual/bash.html#Shell-Arithmetic'>Bash's own arithmetic expressions</a>.</li>
                            <li>
                                <p>
                                    <b>BREAKING</b>: Shifted to a new naming convention for variables that hold additional data related to options. The new format for the names of such variables is <code>optdata&lowbar;&lowbar;&lt;opt_name&gt;&lowbar;&lowbar;&lt;optdata_name&gt;</code> where <code>&lt;opt_name&gt;</code> is the name of the option, and <code>&lt;optdata_name&gt;</code> is the name of the piece of option data that the variable holds. Note the double underscore (<code>&lowbar;&lowbar;</code>) surrounding the <code>&lt;opt_name&gt;</code>.
                                </p>
                                <p>
                                    This prevents conflating the main option variables (<code>opt_&lt;opt_name&gt;</code>) with the variables that hold additional option data, and allows for easy access to variables from either set via the <code>${!prefix&ast;}</code> and <code>${!prefix@}</code> <a href='https://www.gnu.org/software/bash/manual/bash.html#Shell-Parameter-Expansion'>parameter expansions</a>.
                                </p>
                            </li>
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

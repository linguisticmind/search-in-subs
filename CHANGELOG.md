# search-in-subs changelog

<table>
    <tr>
        <th>Version</th>
        <th>Date</th>
        <th>Description</th>
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

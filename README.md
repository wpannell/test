# test
Arguments may be given for each token in the form name="value" for strings and in the form name=value for booleans and numbers. In string arguments, escape ", \, and line terminators (\n or \r\n) with a \, e.g. arg1="\"quoted\""; arg2="c:\\path"; and arg3="one\ntwo". The brackets may be omitted if there are no arguments.

Examples: $TOKEN, ${TOKEN}, ${TOKEN, count=100}, ${ENV, var="PATH"}

Project Tokens

${DEFAULT_SUBJECT}
This is the default email subject that is configured in Jenkinss system configuration page.
${DEFAULT_CONTENT}
This is the default email content that is configured in Jenkinss system configuration page.
${DEFAULT_PRESEND_SCRIPT}
This is the default pre-send script content that is configured in Jenkinss system configuration. This is the only token supported in the pre-send script entry field.
${PROJECT_DEFAULT_SUBJECT}
This is the default email subject for this project. The result of using this token in the advanced configuration is what is in the Default Subject field above. WARNING: Do not use this token in the Default Subject or Content fields. Doing this has an undefined result.
${PROJECT_DEFAULT_CONTENT}
This is the default email content for this project. The result of using this token in the advanced configuration is what is in the Default Content field above. WARNING: Do not use this token in the Default Subject or Content fields. Doing this has an undefined result.

Extended Email Publisher Specific Tokens

${CHANGES_SINCE_LAST_SUCCESS}
Displays the changes since the last successful build.
reverse
If true, show most recent builds at the top instead of the bottom. Defaults to false.
format
For each build listed, a string containing %X, where %X is one of
%c
changes
%n
build number
Defaults to Changes for Build #%n\n%c\n

See additional documentation on ${CHANGES} token for showPaths, format and pathFormat parameters
${PROJECT_NAME}
Displays the project's full name. (See AbstractProject.getFullDisplayName)
${PROJECT_DISPLAY_NAME}
Displays the project's display name. (See AbstractProject.getDisplayName)
${CHANGES}
Displays the changes since the last build.
showDependencies
If true, changes to projects this build depends on are shown. Defaults to false
showPaths
If true, the paths, modified by a commit are shown. Defaults to false
format
For each commit listed, a string containing %X, where %x is one of:
%a
author
%d
date
%m
message
%p
path
%r
revision
Not all revision systems support %d and %r. If specified showPaths argument is ignored. Defaults to "[%a] %m\\n"

pathFormat
A string containing %p to indicate how to print paths. Defaults to "\\t%p\\n"
regex
A regular expression.
replace
A replacement for all substrings of the change message that match the given regular expression.
${TEST_COUNTS,var="TYPE"}
Displays the number of tests based on the type (var) passed in (total, pass, fail, skip). Defaults to total.
${JOB_DESCRIPTION}
Displays the description of the job.
${PROJECT_URL}
Displays a URL to the project's page.
${CHANGES_SINCE_LAST_UNSTABLE}
Expands to the changes since the last unstable or successful build.
reverse
If true, show most recent builds at the top instead of the bottom. Defaults to false.
format
For each build listed, a string containing %X, where %X is one of
%c
changes
%n
build number
Defaults to Changes for Build #%n\n%c\n

See additional documentation on ${CHANGES} token for showPaths, format and pathFormat parameters
${BUILD_LOG_MULTILINE_REGEX}
Displays build log segments that match the regular expression.
regex
java.util.regex.Pattern
Segments of the build log that match this regular expression are included. See also null. No default. Required parameter
maxMatches
The maximum number of matches to include. If 0, all matches will be included. Defaults to 0.
showTruncatedLines
If true, include [...truncated ### lines...] lines. Defaults to true.
substText
If non-null, insert this text into the email rather than the entire segment. Defaults to null.
escapeHtml
If true, escape HTML. Defaults to false.
matchedSegmentHtmlStyle
If non-null, output HTML. Matched lines will become <b style="your-style-value">html escaped matched lines</b>. Defaults to null.
${FILE,path="PATH"}
Includes the content of a specified file (path) relative to the workspace root.
${BUILD_NUMBER}
Displays the number of the current build.
${JENKINS_URL}
Displays the URL to the Jenkins server. (You can change this on the system configuration page.)
${BUILD_ID}
Displays the build ID of the current build.
${FAILED_TESTS}
Displays failing unit test information, if any tests failed.
showStack
Shows stack trace in failing test output. Defaults to true.
showMessage
Shows error message in failing test output. Defaults to true.
maxTests
Display at most this many tests. No limit is set by default.
onlyRegressions
Display only the failing tests that are different from previous builds. Defaults to false.
${BUILD_LOG_EXCERPT}
Displays an excerpt from the build log.
start
Regular expression to match the excerpt starting line (matching line is excluded).
end
Regular expression to match the excerpt ending line (matching line is excluded).
See java.util.regex.Pattern
${CAUSE}
Displays the cause of the build.
${SVN_REVISION}
Displays the subversion revision number. Also supports the SVN_REVISION_n version the Subversion plugin exports.
${SCRIPT}
Custom message content generated from a groovy script.Custom scripts should be placed in "$JENKINS_HOME/email-templates". When using a custom script the plugin will look in the resources forthe email-ext plugin first, and then in the $JENKINS_HOME/email-templatesdirectory. No other directories will be searched.You may also use the Config File Provider plugin to manage your scripts. Prefix the managed file NAME with "managed:" for the template or script parameter. Example: ${SCRIPT, template="managed:ManagedFileName"}
script
When this is used, only the last value in the script will be used in the expansion (script and template can not be used together).
template
The template in Groovy's SimpleTemplateEngine format.
${JELLY_SCRIPT,template="TEMPLATE_NAME"}
Custom message content generated from a Jelly script template. There are two templates provided: "html" and "text". Custom Jelly templates should be placed in $JENKINS_HOME/email-templates.When using custom templates, the template filename without ".jelly" should be used for the "template" argument.You may also use the Config File Provider plugin to manage your templates. Prefix the managed file NAME with "managed:" for the template parameter. Example: ${JELLY_SCRIPT, template="managed:ManagedFileName"}
${BUILD_LOG}
Displays the end of the build log.
maxLines
Display at most this many lines of the log. Defaults to 250.
escapeHtml
If true, HTML is escape. Defaults to false.
${BUILD_URL}
Displays the URL to the current build.
${BUILD_STATUS}
Displays the status of the current build. (failing, success, etc...)
${BUILD_LOG_REGEX}
Displays lines from the build log that match the regular expression.
regex
Lines that match this regular expression are included. See also java.util.regex.Pattern.Defaults to "(?i)\\b(error|exception|fatal|fail(ed|ure)|un(defined|resolved))\\b"
linesBefore
The number of lines to include before the matching line. Lines that overlap with another match or linesAfter are only inlcuded once. Defaults to 0.
linesAfter
The number of lines to include after the matching line. Lines that overlap with another match or linesBefore are only included once. Defaults to 0.
maxMatches
The maximum number of matches to include. If 0, all matches will be included. Defaults to 0.
showTruncatedLines
If true, include [...truncated ### lines...] lines. Defaults to true.
substText
If non-null, insert this text into the email rather than the entire line. Defaults to null.
escapeHtml
If true, escape HTML. Defauts to false.
matchedLineHtmlStyle
If non-null, output HTML. Matched lines will become <b style="your-style-value"> html escaped matched line</b>. Defaults to null.
addNewline
If true, adds a newline after subsText. Defaults to true.
defaultValue
This value will be used if nothing is replaced.

Token Macro Plugin Tokens

${GIT_BRANCH}
Expands to the name of the branch that was built.
Parameters

all
If specified, all the branches that point to the given commit is listed. By default, the token expands to just one of them.
fullName
If specified, this token expands to the full branch name, such as 'origin/master'. Otherwise, it only expands to the short name, such as 'master'.
${GIT_REVISION}
Expands to the Git SHA1 commit ID that points to the commit that was built.
Parameters

length=N (optional, default to 40)
Specify the commit ID length. Full SHA1 commit ID is 40 character long, but it is common to cut it off at 8 or 12 as that often provide enough uniqueness and is a lot more legible.
${BUILD_NUMBER}
Expands to the current build number, a sequential auto-incrementing unique number that identifies the build, such as "125"
${ENV,var="VARIABLENAME"}
Expands to an environment variable (specified here as VARIABLENAME) from the build environment. Note that this does not include any variables set by the build scripts themselves, only those set by Jenkins and other plugins.
${PROPFILE,file="FILENAME",property="PROPERTYNAME"}
Expands to the value of a property in a property file. The filename is relative to the build workspace root.

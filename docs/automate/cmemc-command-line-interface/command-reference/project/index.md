---
title: "cmemc: Command Group - project"
description: "List, import, export, create, delete or open projects."
icon: octicons/file-directory-24
tags:
  - Project
  - cmemc
---
# project Command Group
<!-- This file was generated - DO NOT CHANGE IT MANUALLY -->

List, import, export, create, delete or open projects.

Projects are identified by a `PROJECT_ID`.

!!! note
    The get a list of existing projects, execute the `project list` command or use tab-completion.



## project open

Open projects in the browser.

```shell-session title="Usage"
$ cmemc project open PROJECT_IDS...
```




With this command, you can open a project in the workspace in your browser to change them.

The command accepts multiple projects IDs which results in opening multiple browser tabs.



## project list

List available projects.

```shell-session title="Usage"
$ cmemc project list [OPTIONS]
```




Outputs a list of project IDs which can be used as reference for the project create, delete, export and import commands.



??? info "Options"
    ```text

    --raw       Outputs raw JSON.
    --id-only   Lists only project identifier and no labels or other meta data.
                This is useful for piping the IDs into other commands.
    ```

## project export

Export project(s) to file(s).

```shell-session title="Usage"
$ cmemc project export [OPTIONS] [PROJECT_IDS]...
```




Projects can be exported with different export formats. The default type is a zip archive which includes metadata as well as dataset resources. If more than one project is exported, a file is created for each project. By default, these files are created in the current directory and with a descriptive name (see `--template` option default).

!!! note
    Projects can be listed by using the `project list` command.


You can use the template string to create subdirectories.

```shell-session title="Example"
$ cmemc config list | parallel -I% cmemc -c % project export --all -t "dump/{{connection}}/{{date}}-{{id}}.project"
```




??? info "Options"
    ```text

    -a, --all                     Export all projects.
    -o, --overwrite               Overwrite existing files. This is a dangerous
                                  option, so use it with care.
  
    --output-dir DIRECTORY        The base directory, where the project files
                                  will be created. If this directory does not
                                  exist, it will be silently created.  [default:
                                  .]
  
    --type TEXT                   Type of the exported project file(s). Use the
                                  --help-types option or tab completion to see a
                                  list of possible types.  [default: xmlZip]
  
    -t, --filename-template TEXT  Template for the export file name(s). Possible
                                  placeholders are (Jinja2): {{id}} (the project
                                  ID), {{connection}} (from the --connection
                                  option) and {{date}} (the current date as
                                  YYYY-MM-DD). The file suffix will be appended.
                                  Needed directories will be created.  [default:
                                  {{date}}-{{connection}}-{{id}}.project]
  
    --extract                     Export projects to a directory structure
                                  instead of a ZIP archive. Note that the
                                  --filename-template option is ignored here.
                                  Instead, a sub-directory per exported project
                                  is created under the output directory. Also
                                  note that not all export types are
                                  extractable.
  
    --help-types                  Lists all possible export types.
    ```

## project import

Import a project from a file or directory.

```shell-session title="Usage"
$ cmemc project import [OPTIONS] PATH [PROJECT_ID]
```




```shell-session title="Example"
$ cmemc project import my_project.zip my_project
```




??? info "Options"
    ```text

    -o, --overwrite  Overwrite an existing project. This is a dangerous option,
                     so use it with care.
    ```

## project delete

Delete project(s).

```shell-session title="Usage"
$ cmemc project delete [OPTIONS] [PROJECT_IDS]...
```




This deletes existing data integration projects from Corporate Memory.

!!! warning
    Projects will be deleted without prompting!


!!! note
    Projects can be listed by using the `project list` command.




??? info "Options"
    ```text

    -a, --all   Delete all projects. This is a dangerous option, so use it with
                care.
    ```

## project create

Create empty new project(s).

```shell-session title="Usage"
$ cmemc project create PROJECT_IDS...
```




This creates one or more new projects. Existing projects will not be overwritten.

!!! note
    Projects can be listed by using the `project list` command.





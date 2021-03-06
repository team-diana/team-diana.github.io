# Computer Science Development Guidelines

A brief introduction to the general guidelines for the
computer science group.

The main purpose of this document is to improve the workflow between the different members of the team.

_Please consider that this document can change in any moment in the future and that improvement may be needed._

---

# Team Communications

## Slack
It is the main communication system of the team. For public messages, please, write in English.

- Use the proper channel
- Be clear
- Prefer the use of _threads_ or _emoji_ to answer to a specific message
- Prefer to upload files to the team's Google Drive and link them in the message (Slack storage is limited)

## Trello
For a general overview, first, see [Trello for software development](http://buildbettersoftware.com/trello-for-software-development)

The following description is made for the _Computer Science_ group (for other sections, the boards could be organised in a slightly different way).

In each _board_, there are several _lists_.

In each list, tasks are represented by _tickets_.

Each ticket has several _fields_.

The lists are:

| Trello Lists | Description |
| ----------- | ----------- |
| `Backlog` | Tasks that need to be done but not yet or that have just not enough detail yet. |
|`Next` | All the task that can be picked by anyone to be completed |
| `In progress` | Move the task from `Next` to this list to inform that the task is been taken charge and is _in progress_. Then open the task’s ticket and in the _Member_ section add your name. In the _Due Date_ section add an estimation of when you think you’ll be able to complete the task. |
|`Staged`	| When you are done, move the ticket here and report it to *Slack*. All the tasks in this list have to be tested. If the test failed, it will come back to `Next` and a special tag will be added. |
| `Approved` | Tests are OK. Waiting to go in _production_ phase (for example, merged to master or to be ordered online). |
| `Live` | Task successfully completed. It will be periodically archived (in the title will be added a date) and a new _Live_ list will be created (to keep the board clean). |

Every ticket begins with [number] that indicate the presumed difficulty level (from 1 - easy to 6 - very hard).
ex: `[2] Design rubber ducks`

If you add a new ticket, be as understandable as possible!
Prefer clearer description than to synthesized ones.

### Start A Task

All the tasks in the `Next` list need to be done. They are ordered per priority (top is the highest priority - bottom is the lowest priority).

If you want to take care of a task from the `Next` list, you have to:

- move the corresponding ticket onto the **top** of `In Progress` list
- open the ticket and add your name to the _Members_ filed
- add in the field _Due Date_ the deadline date on which you think to complete the task.

### Work On A Task

You can write messages and add other details to the ticket. It is preferable to use the _checklists_ feature to make the other members know the current task progress status.
Use multiple checklists to make clear of the different parts of the task.

You can mention people by writing `@nameofsomeone` in the field

### End A Task

You have to:

- tick the deadline box
- move the ticket from `In Progress` onto the **top** of `Staged`
- notify in the proper channel on **Slack**

### In Case Of Issue
- Tag it with the Red Tag `Feedback Request`
- Move the ticket onto the top of `Staged` list

### What Will Happen Later

The

---

# Git

## New repository

- If it's a repo containing code for a specific rover put the rover name before the repo name (i.e. T0R0-ArmDriver). The rover code name is written in `UPPERCASE`, followed by a `-` and by the repo name written in `UpperCamelCase`.
- If it's a general repo use a meaningful name written in `UpperCamelCase`.
- Create the basic documentation files (See _Documentation_)

## Documentation

Always make sure to have in your project root folder these files:

* README.md
* CHANGELOG.md
* LICENCE

### Readme file
It must contain:

* Repository **description** and **purpose**
* System **Requirements**
* **Compilation** instructions
* **Run** instruction
* Eventually, instructions to generate **automatic documentation** (i.e. doxygen)
* **References** (if used)

### Changelog file

It has to contain all the changes made.
If the software has not a version number yet, write changes to **[Unreleased]** section. When version number will be assigned, Unreleased content will be moved to proper tag.
Always keep the Unreleased tag, even though it is empty.

Even though this process will be automatic in the future of the team with the help of some developing tools, you can read [Keep a Changelog](https://keepachangelog.com/en/1.0.0/) for an introduction.

Candidate tools:
- [conventional-changelog-cli](https://github.com/conventional-changelog/conventional-changelog/tree/master/packages/conventional-changelog-cli)

### Licence
Use the _MIT licence_ format:

```
MIT License

Copyright (c) 2020 Team DIANA at Politecnico di Torino.

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

```

## Branches

The two main branches are `master` and `develop`. The existance and usage of this two branches are **mandatory**.

`master` contains always the last version of the working software.

`develop` contains the experimental software that waits for validation.

To add a feature, create a branch from `develop` and give it a proper name describing the type of operation.
When finished, make a general refactor of the code, complete the documentation and merge to `develop`. After that, your branch will be deleted by the remote repository.

Before merging into `develop` the code **must** be:
- refactored
- readable
- compleated with meaningful comments
- provided with a complete and easy to understand documentation

### Validation od `develop`

Periodically, `develop` will be reviewed by one of the repository responsibles for validation. In this phase, the code will be double-checked, reviewed and tested. If the validation process pass all the tests, the `develop` branch will be marged with `master` and version numers will be increased accordingly (and a tag will be created). Otherwise, changes are required and feedback will be communicated with the members working on the repository.

**REMEMBER!** that only the responsibles of the repository are allowed to merge `develop` onto `master`. This because, this procedure corresponds to a safety level and aim to avoid that faulty software can cause damage to the rover. Only versions on `master` are going to be used in the rover.

Branches names could be:

| branch name           | circustancies                                      |
| --------------------- | -------------------------------------------------- |
| `master`              | contains always the last working code.             |
| `develop`             | keep track of the experimental software.           |
| `feature/description` | generic changes will be made (`feat`, `fix`, `refactor`, `docs`, ...) |
| `fix/description`  | a fix directly made to `develop`                   |
| `hotfix/description`  | a fix directly made to `master`                    |
| `release/description` | minor changes before merging `develop` to `master`  (used usually to complete documentation and final tests) |

 replace _description_ accordingly to what you have to do.

 **All the branches**, with the exception of `master` and `develop`, **will be deleted from the remote repository after merging into or rebasing onto another branch**.

## Commits

See this for reference [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0-beta.4/)

Use this syntax

```
<type>(optional scope or subsystem): <description>

[optional body]

[optional footer]
```

**type** describes the change type and it could be:

* `feat`
* `fix`
* `refactor`
* `style`
* `docs`
* `test`
* `perf`
* `chore`

Use always the second-person singular, present time.

For example:

```
feat(autopilot): add path input from MQTT
------------
Coordinates are received from MQTT network and passed to the
pilot instance for trajectory planning.
```

**For a complete description check this link** [git commit guidelines](https://www.conventionalcommits.org/en/v1.0.0-beta.2/).

---

# Software basic rules

1. Design it first
2. Keep it simple
3. Keep it modular
4. Keep it maintainable
5. Test it
6. Document it

# Coding rules

## Set up your editor or IDE first

### Indentation

**Spaces and Tabs.**
_Use 4 spaces_ to indent code. If your editor/IDE is good, it has a feature that automatically uses a certain amount of spaces when TAB key is pressed. Set this feature up to better work with the other member of the team.

Spaces will be shown the same on all the editors. Four is an optimal and one of the most used standards around the world (two is not enough, six is too much).

**Brackets.**
For better readability and as a standard for the team use this kind of indentation for brackets:

```C
if (!condition_1) {
	printf("hello");
	if (!condition_2) {
		printf("world");
	}
}
```

**Readability**
Use the indentation to improve readability of the code.
_You shall not exagerate_.
For example line up variables values that have some common context:

```C++
int meaningful_name_for_variable_1 = 1;
int meaningful_name_for__2 = 3;

float another_meaningful_name_variable     = 3.14;
float different_meaningful_name_variable   = 1.1618;

foo (meaningful_name_for_variable_1, meaningful_name_for_variable_2);
foo (another_meaningful_name_variable, different_meaningful_name_variable);
```

## Good Practices

### Comments
Use a comment to describe briefly the logic of a part of the code.
Preferably, use _Doxygen_ format for C/C++ or _JavaDoc_ for Java.

Comments need to be:

- Simple
- Understandable
- Easily Readable

### Naming Conventions
Use simple and meaningful names inside the code.
The name shall describe briefly what the code entity does.

**For C++**

| Code entity | Syntax                  |
| ----------- | ----------------------- |
| Namespaces  | `camelCase`            |
| Macros      | `SCREAMING_SNAKE_CASE`  |
| Classes     | `PascalCase`            |
| Structs     | `PascalCase`            |
| Enums       | `camelCase`             |
| Enumerators | `camelCase`            |
| Typedef     | `camelCase`             |
| Unions      | `camelCase`             |
| Methods     | `camelCase`             |
| Fields      | `camelCase`             |
| Global Functions | `camelCase`        |
| Global Variables | `snake_case`       |
| Parameters  | `snake_case`            |
| Variables   | `snake_case`            |

Code Example:

```C++
#if !defined(OS)
#define OS_NOT_DEFINED
#endif

/*********************************************
* ...globalFunc...
*********************************************/
void globalFunc();

namespace foo {
    /**
    ...Foo...
    */
    class Foo {
    public:
        Foo();

        ~Foo();

        virtual Foo *getSelf() { return Foo::getSelf(); }

    private:
        void innerFunc();

        int var;
    };
}
struct FooPOD {
#ifdef OS_NOT_DEFINED
#define OS "unknown"
#endif
#define FooPOD_OS OS
    int i;
};
struct FooC {
private:
    int i;
};
extern int a;

static int innerFunc();

int a = innerFunc();

int innerFunc() { return 5; }

void foo::Foo::innerFunc() {
    label1:
    int continuation = 0xCD
                       + 0xFD + 0xBAADF00D + 0xDEADBEEF;
    auto la = [](int i1, int i2) -> bool mutable {
        label2:
        return i1 < i2;
    }(1, 2);
}
```

If you need to pass a variable inside a class constructor and it needs to be stored inside the class, you can use the following method.

```C++
class Foo::Foo (int _var1, float _var2)
{
	var1 = _var1;		// var1 is an integer
	var2 = _var2;		// var2 is a floating-point
}
```

### Directories Structure

Code must be in a directory separated from the other software parts.

A generic example:

**For C++**


```
.
├── CHANGELOG.md
├── LICENSE
├── Makefile
├── README.md
├── doc
│   └──
├── dox.url
├── doxygen
│   ├── diana_logo_doxygen.jpg
│   └── doxConf
├── images
│   └──
└── src
    ├── CmakeLists.txt
    ├── build
    │   └──
    ├── other1.cpp
    ├── other1.hpp
    └── main.cpp
```

For other programming languages, use a similar structure.

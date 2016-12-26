# Development Coding standards

## All Code
* Please use Linux line-endings (LF, no CR).
* Please try to keep diff minimal. If you really feel some re-formatting is necessary, please do it in a separate commit to ease review
* Keep lines reasonably short (80 chars is a good guide), break statements over multiple lines where necessary
* Use `default` cases in `switch` statements only where you __really__ intend it, they neuter compile-time checking of missed code when new enumerations are introduced

## Flight Code (C)
The flight side code has historically tried to stick as much as possible with the [linux kernel style](https://www.kernel.org/doc/Documentation/CodingStyle).

### New Draft Guidelines
Always defer to K&R conventions when not explicitly covered here.
* Use TABS, not spaces
* Use typedefs only when strictly necessary
    - One exception is for device handles where they appear in public declarations of PiOS drivers
* `case` statements are indented at the same level as the parent `switch`
* Use spaces around parentheses for `if`, `switch`, etc., but not for functions.
* Opening braces are on the same line as `if`, `switch`, etc. `else` is on the same line as previous closing brace, e.g.

    ```c
    if (this_thing) {
        switch (this_thing) {
        case THING_1:
            do_some_stuff();
            break;
        case THING_2:
            do_other_stuff();
            break;
        }
    } else {
        do_that_other_thing();
    }
    ```

* Braces are optional for single statement `if`s, but ONLY if all branches have no braces. e.g. Okay:

    ```c
    if (this_thing)
        do_stuff();
    else if (other_thing)
        do_other_stuff();
    else
        return NULL;
    ```

    NOT okay:

    ```c
    if (this_thing)
        do_stuff();
    else {
        PIOS_DEBUG_Assert(false);
        return NULL;
    }
    ```
* ... more to come ...

## GCS Code (C++)
Use [Qt style](http://wiki.qt-project.org/Coding_Style) and [Qt coding conventions](http://wiki.qt-project.org/Coding_Conventions)

* Use 4 SPACES, not tabs
* DON'T assume that returned pointers are non-null
* Use [dynamic UAVO relations](./uavo_widget_relations.md) where you can, these will (soon) be checked at compile time against UAVO definitions

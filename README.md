# squirrel-snippets

Some squirrel snippets, with an Electric Imp flavour.

## Formatting a date

Format a date, suitable for parsing by JavaScript.

    // Format a date (assumed to be UTC), suitable for parsing by JavaScript.
    // e.g. "2012-04-23T18:25:43.511Z"
    function format_date(d) {
        return format("%04d-%02d-%02dT%02d:%02d:%02d.%03dZ",
            d.year, d.month, d.day,
            d.hour, d.min, d.sec, d.usec / 1000);
    }

## Displaying a squirrel table

    foreach (k, v in t) {
        print(k + ": " + v + "\n");
    }

## Elapsed time, in milliseconds

    function elapsed_ms(d1, d2) {
        // Scale d1 and d2 into milliseconds;
        // doesn't matter what they're relative to,
        // as long as they overflow appropriately.
        local m1 = (d1.time * 1000) + (d1.usec / 1000);
        local m2 = (d2.time * 1000) + (d2.usec / 1000);

        return m2 - m1;
    }

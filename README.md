# tepa-zoned-time

[![test](https://github.com/arowM/tepa-zoned-time/actions/workflows/test.yaml/badge.svg)](https://github.com/arowM/tepa-zoned-time/actions/workflows/test.yaml) [![Elm package](https://img.shields.io/elm-package/v/arowM/tepa-zoned-time)](https://package.elm-lang.org/packages/arowM/tepa-zoned-time/latest/)

TEPA library to handle zoned time.

# A Quick Example

## Construct `ZonedTime`

```elm
import Tepa.Time as Time

-- 1970-01-04T13:54:12.123Z
original : ZonedTime
original = fromPosix Time.utc (Time.millisToPosix 309252123)

midnight : ZonedTime
midnight = setToMidnight original
```

```elm
sample : Maybe ZonedTime
sample =
    fromGregorianUtc
        { year = 2000
        , month = Time.Jun
        , day = 10
        }
        |> Maybe.map (addHours 22)
        |> Maybe.map (addMinutes 33)
        |> Maybe.map (addSeconds 44)
        |> Maybe.map (addMillis 55)
```

## Unwrap `ZonedTime`

```elm
import Tepa.Time as Time

posix : Maybe Time.Posix
posix =
    sample
        |> Maybe.map toPosix

zone : Maybe Time.Zone
zone =
    sample
        |> Maybe.map toZone
```

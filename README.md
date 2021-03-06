# Dictionaries

In computer science, an associative array, map, symbol table, or dictionary is an abstract data type composed of a collection of (key, value) pairs, such that each possible key appears at most once in the collection.

From [Wikipedia](https://en.wikipedia.org/wiki/Associative_array).

## Running

For all benchmarks:

    $ stack bench :space

For just space:

    $ stack bench :space

For just time:

    $ stack bench :time

## Insert Int keys


|Case|                                              Bytes|    GCs|
|---|---|---|
|Data.Map.Strict.insert mempty                        |64      |0  |
|Data.Map.Lazy.insert mempty                          |64      |0  |
|Data.HashMap.Strict.insert mempty                    |64      |0  |
|Data.HashMap.Lazy.insert mempty                      |48      |0  |


## From List Int keys


|Case|                                              Bytes|    GCs|
|---|---|---|
|Data.Map.Strict.fromList     (1 million)|  1,016,187,152  |1,942  |
|Data.Map.Lazy.fromList       (1 million)|  1,016,187,152  |1,942  |
|Data.IntMap.Strict.fromList  (1 million)|    776,852,648  |1,489  |
|Data.IntMap.Lazy.fromList    (1 million)|    776,852,648  |1,489  |
|Data.HashMap.Strict.fromList (1 million)|    161,155,384    |314  |
|Data.HashMap.Lazy.fromList   (1 million)|    161,155,384    |314  |


<!-- RESULTS -->

## Lookup Int (Randomized)

|Name|10|100|1000|10000|
|---|---|---|---|---|
|Data.Map.Lazy|26.62 ns|34.21 ns|43.12 ns|55.55 ns|
|Data.Map.Strict|26.49 ns|34.15 ns|42.73 ns|56.03 ns|
|Data.HashMap.Lazy|22.03 ns|23.70 ns|17.96 ns|24.86 ns|
|Data.HashMap.Strict|21.05 ns|23.71 ns|17.80 ns|24.95 ns|
|Data.IntMap.Lazy|17.17 ns|25.39 ns|32.74 ns|43.08 ns|
|Data.IntMap.Strict|16.93 ns|25.42 ns|32.93 ns|42.92 ns|

## Insert Int (Randomized)

|Name|10|100|1000|10000|
|---|---|---|---|---|
|Data.Map.Lazy|607.1 ns|11.91 μs|247.7 μs|4.226 ms|
|Data.Map.Strict|726.2 ns|13.69 μs|269.1 μs|4.575 ms|
|Data.HashMap.Lazy|534.0 ns|6.706 μs|104.1 μs|3.628 ms|
|Data.HashMap.Strict|525.9 ns|6.644 μs|103.6 μs|3.637 ms|
|Data.IntMap.Lazy|261.5 ns|3.796 μs|55.55 μs|1.788 ms|
|Data.IntMap.Strict|314.8 ns|4.558 μs|66.16 μs|1.943 ms|

## FromList ByteString (Monotonic)

|Name|10000|
|---|---|
|Data.Map.Lazy|6.214 ms|
|Data.Map.Strict|6.425 ms|
|Data.HashMap.Lazy|3.198 ms|
|Data.HashMap.Strict|3.240 ms|
|Data.Trie|15.80 ms|

## FromList ByteString (Randomized)

|Name|10|100|1000|10000|
|---|---|---|---|---|
|Data.Map.Lazy|802.2 ns|17.19 μs|361.8 μs|8.774 ms|
|Data.Map.Strict|866.4 ns|18.31 μs|370.9 μs|8.919 ms|
|Data.HashMap.Lazy|819.2 ns|10.54 μs|147.2 μs|3.784 ms|
|Data.HashMap.Strict|871.5 ns|10.70 μs|149.0 μs|3.801 ms|
|Data.Trie|1182 ns|24.94 μs|1174 μs|25.13 ms|

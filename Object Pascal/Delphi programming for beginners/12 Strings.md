[[Object Pascal/Delphi programming for beginners/_ 0 intro]]

#delphi/string

# String
>[!note] string
>It is a sequence of symboles inside single quotes
>to declare string variable, you have to use type `String`

contcatenation: `a string + a string`
comparison: `> <`, `'AB' > 'AA'`, `'DC' > 'ABCDE'`

## String Procedures
### Delete
`Delete(St, Pos, N)`
`St: string`
`Pos, N: integer`
Delete `N` symbols from string `St`, starting from positions `Pos`.
Examples:
`Delete('abcdef', 4, 2)` -> `'abcf'`
`Delete('Turbo-Pascal', 1, 6)` -> `Pascal`

### Insert
`Insert(St1, St2, Pos)`
`St1, St2: string`
`Pos : integer`
Insert symbols of string `St1` into string `St2` starting from position `Pos`
Examples:
`Insert('Turbo', '-Pascal', 1)` -> `Turbo-Pascal`
`Insert('-Pascal', 'Turbo', 6)` -> `Turbo-Pascal`

### Copy
`Copy(St, Poz, N)`
St: string
Pos, N: integer
Result it the copy od N symbols from string St starting from position Pos
`Copy('abcdefg', 2,3) ;` -> 'bcd'


### Length
`Length(abcdefg)` -> 7


### Pos
`Pos('de','abcdef')` -> 4
`Pos('r', 'abcdef')` -> 0









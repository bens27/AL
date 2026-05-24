# AL Development Reference

Condensed from Microsoft AL Guidelines Vibe Coding Rules.

## Naming

**Objects:** PascalCase, descriptive, max 26 chars for name (+ affix space).

**Files:** `ObjectName.ObjectType.al` — e.g., `SalesHeader.Table.al`, `CustomerCard.PageExt.al`

**Interfaces:** prefix `I` (e.g., `ICustomerService.Interface.al`); implementations use `Impl` suffix.

**Event subscriber parameters:** use specific names like `SalesHeader`, `Customer` — not generic `Rec`.

## Code Style

- Feature-based folders: `src/Feature/SubFeature/` not `Tables/`, `Pages/`
- `if`/`else`/`repeat`/`for`/`while`/`case`/`end` start their own line
- Small focused procedures; `local` for internal logic
- XML docs on public codeunit procedures

## Performance Patterns

```al
// Filter early + SetLoadFields before find
Customer.SetRange(City, CityFilter);
Customer.SetLoadFields(Name, "Credit Limit (LCY)");
if Customer.FindSet() then
  repeat
    // ...
  until Customer.Next() = 0;

// Set-based aggregation
CustLedgerEntry.SetRange("Customer No.", CustomerNo);
CustLedgerEntry.CalcSums(Amount);
```

## Error Handling Patterns

```al
var
  CustomerNotFoundErr: Label 'Customer %1 does not exist.', Comment = '%1 = Customer No.';

[TryFunction]
local procedure TryExternalCall()
begin
  // operation that may fail
end;

if not TryExternalCall() then
  Error(CustomerNotFoundErr, CustomerNo);
```

## AL-Go Structure

| Project | Contains |
|---------|----------|
| App | Tables, pages, codeunits, reports |
| Test | Test codeunits only; references App |

Never mix application and test code in the same project.

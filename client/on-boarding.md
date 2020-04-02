## On-boarding a Client (Employer)
### Import Employee List

#### Fresh new list with no pre-existing-employees in the system.

#### Not a fresh new list -> Add a new list to a list with pre-existing employees.
Expected behaviours:
- Non-existing NRICs: Added
- Existing NRICs:the current record gets updated
  - Current Balance: Updated as following:
    - ggg

Prepare excep file
`=IF(E2="M","Male",IF(E2="F","Female",""))`

[Sample Employee Input List](assets/sample-mrbean-existing-list-update_input.xls) 
[Sample Employee List](assets/sample-mrbean-existing-list-update.xls) 

# ClaimApprover
## BusinessClaimApprover
This is an Entity Role for Organisations/Entities who have employees to do the checking or approvals.
### approvalPrincipals: ApprovalPrincipal

### employers

## ApprovalPrincipal

# Organisation
## Position (IndividualMember)
### canApproveEmployer(employer: BusinessEmployer)
- if hasRole(CLAIM_APPROVER)
    -  set bca = organisation.businessClaimApprover
    - if bca.approvalPrincipals.count() === 0 
        - then return true
    - else if  

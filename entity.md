# . Claim
## .. ClaimApprover
### ... user: User *ManyToOne
- A ClaimApprover may either be a freelance or an employee but they all have a user associated with.
### ... position: Position
- A Position may belong to 
    - **the BusinessEmployer** for which the approver is doing the checking.
         - => approver is **_internal_** 
         - => `position.employer === employer.organisation`
    - **the BusinessClaimApprover** who is performing the checking service for the employer.
        - => approver is **_external_** 
        - => `position.employer !== employer.organisation`
        - => `position.hasRole(ROLE_APPROVER) === true`
        
 


# . ClaimApprover
## .. BusinessClaimApprover
- This is an Entity Role for Organisations/Entities who have employees to do the checking or approvals.
### ... approvalPrincipals: ApprovalPrincipal

### ... employers

## .. ApprovalPrincipal

# . Organisation
## .. Position (IndividualMember)
### ... canApproveEmployer(employer: BusinessEmployer)
- if hasRole(CLAIM_APPROVER)
    -  set bca = organisation.businessClaimApprover
    - if bca.approvalPrincipals.count() === 0 
        - then return true
    - else if  

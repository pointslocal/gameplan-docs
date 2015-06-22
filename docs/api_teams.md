# /api/v1/teams
### GET

##### Request Parameters
- sport **[ string ]** - Sport name or GUID
- school **[ string ]** - School's name or internal GUID
- guid **[ string ]** - Sport's internal GUID
- season **[ enum ]** - Applicable season(s)
- guid **[ string ]** - Team's GUID

##### Response Parameters
- guid **[ string ]** - Team's internal GUID
- school **[ string ]** - Team's school name
- school_guid **[ string ]** - School's internal GUID
- sport **[ string ]** - Team's sport

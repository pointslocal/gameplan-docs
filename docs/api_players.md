# /api/v1/players
### GET

##### Request Parameters
- search **[ string ]** - Freeform search text, matches player's name or school
- position **[ string ]** - Filters by position GUID
- active_year **[ int ]** - Active year
- grad_year **[ int ]** - Graduation year of player
- guid **[ string ]** - Player's GUID

##### Response Parameters
- guid **[ string ]** - Player's GUID
- name **[ string ]** - Player's full name
- firstname **[ string ]** - Player's first name
- lastname **[ string ]** - Player's last name
- schools **[ array ]** - Schools to which player belongs
- meta **[ array ]** - An array of player metadata
- sports **[ array ]** - List of sports the player is connected
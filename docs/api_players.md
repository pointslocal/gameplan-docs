# /api/v1/players
### GET

##### Request Parameters
- search **[ string ]** - Freeform search text, matches player's name or school
- position **[ string ]** - Filters by position GUID

##### Response Parameters
- name **[ string ]** - Player's full name
- firstname **[ string ]** - Player's first name
- lastname **[ string ]** - Player's last name
- schools **[ array ]** - Schools to which player belongs
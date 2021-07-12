# justForTest
``` puml
skinparam linetype ortho
left to right direction

rectangle "Firebase" {
    entity FirebaseAuth {
        UserUid: String
    }
    entity "Firebase RTDB" {
        user/status
        user/channel
        user/role

    }
}

rectangle "DB Server" {
    database RDBMS {
        entity UserInfo {
            UserUid: String
            Name: String
            Birthday: Date
        }
        FirebaseAuth ||--|| UserInfo

        entity UserScore {
            UserScoreId
            UserUid: String
            Date: Datetime
            UpDown: {1, -1}
            Voter: String
            VoteerScore: Int
        }
        FirebaseAuth ||--o{ UserScore

        entity UserBadge {
            UserBadgeId: Int
            UserUid: String
            BadgeId: Int
        }
        FirebaseAuth ||--o{ UserBadge

        entity BadgeList {
            BadgeId: Int
            BadgeName: String
            BadgeImg: String
        }
        UserBadge ||--|| BadgeList

        entity Drink {
            DrinkId: Int
            UserUid: String
            Date: Datetime
            DrinkTypeId: Int
        }
        FirebaseAuth ||--o{ Drink

        entity DrinkType {
            DrinkTypeId: Int
            DrinkName: String
            Manufacturer: String
            AlcoholLevel: Int
            Price: Int
        }
        Drink ||--|| DrinkType

        entity Attendance {
            AttendanceId: Int
            UserUid: String
            ChannelId: String
            Role: {HOST, ...}
            Date: Datetime
        }
        FirebaseAuth ||--o{ Attendance
    }
}
```

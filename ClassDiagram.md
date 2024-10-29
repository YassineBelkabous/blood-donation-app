```mermaid
classDiagram
    class User {
        -string userId
        -string email
        -string password
        -string name
        -string phoneNumber
        -string adress
        +signUp()
        +signIn()
        +updateProfile()
    }

    class Donor {
        -string bloodType
        -date lastDonationDate
        -boolean isAvailable
        +updateAvailability()
        +updateDonationHistory()
        +getDonationHistory()
        +searchNearbyRequests()
        +respondToRequest()
    }

    class Recipient {
        -string bloodType
        -string patientName
        -string hospitalName
        -boolean isUrgent
        +createBloodRequest()
        +searchDonors()
        +contactDonor()
    }

    class BloodRequest {
        -string requestId
        -string bloodType
        -string urgency
        -date requiredDate
        -string hospitalName
        -string location
        +createRequest()
        +updateStatus()
        +cancelRequest()
        +matchDonors()
        +notifyDonors()
    }

    class Appointment {
        -int appointmentId
        -date appointmentDate
        -string location
        +scheduleAppointment()
        +cancelAppointment()
        +sendReminders()
    }

    class Authentication {
        -string email
        -string password
        +verifyEmail()
        +resetPassword()
    }

    class Notification {
        -int notificationId
        -string message
        -date timestamp
        -boolean isRead
        +sendNotification()
        +markAsRead()
        +getNotificationHistory()
    }

    User <|-- Donor
    User <|-- Recipient
    Recipient "1" --> "*" BloodRequest : creates
    Donor "1" --> "*" Appointment : books
    Authentication "1" --> "1" User : authenticates
    BloodRequest "1" --> "*" Donor : matches with
    User "1" --> "*" Notification : receives
    BloodRequest "1" --> "1" Recipient : belongs to
```
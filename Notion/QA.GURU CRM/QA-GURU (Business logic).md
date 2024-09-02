1. **Пользователи (User)**: Пользователи имеют разные роли, включая студентов, наставников, лекторов, менеджеров и администраторов. У пользователей есть информация о профиле, такая как имя, электронная почта, номер телефона и фотография профиля. Роли пользователей могут быть обновлены. Также управление пользователями включает возможность блокировки и разблокировки учетных записей пользователей.
2. **Лекции (Lecture)**: Лекции - это основное образовательное содержимое, которое представляет собой информацию о теме, описание, ссылки на контент, и уровень домашнего задания. Лекции могут быть созданы, обновлены и удалены.
3. **Домашние задания (HomeWork)**: Домашние задания привязаны к лекциям и могут быть отправлены студентами на проверку. Домашние задания могут быть одобрены или отклонены, а также сброшены до исходного состояния.
4. **Комментарии (Comment)**: Комментарии могут быть оставлены к домашним заданиям. Комментарии могут быть созданы, обновлены и удалены.
5. **Тренинги (Training)**: Тренинги - это наборы лекций, сгруппированные вместе. Они включают в себя информацию о наставниках, технологическом стеке и тарифах.
6. **Тарифы (Tariff)**: Тарифы указывают стоимость тренинга и указывают, включено ли выполнение домашних заданий в тариф.
7. **Покупки тренингов (Purchase)**: Пользователи могут приобрести доступ к тренингу на основе выбранного тарифа.

---

В контексте GraphQL, `**input**`, `**enum**` и `**type**` имеют следующие значения:

- `**input**`: Используется для определения структуры данных, которую вы хотите получить от клиента как аргумент для мутаций и запросов. `**input**` представляет собой набор полей, которые могут быть использованы для создания или изменения данных на сервере. Например, в вашей схеме `**UserCreateInput**` используется для получения данных от клиента, которые затем могут быть использованы для создания нового пользователя.
- `**enum**`: Это тип, представляющий ограниченный набор значений. Каждое значение `**enum**` является уникальной строкой. `**enum**` обычно используются для представления определенного набора констант и обеспечения того, что любое значение, входящее или выходящее, находится в этом наборе. Например, `**UserRole**` является перечислением, которое определяет возможные роли пользователя (ADMIN, LECTOR, MANAGER и т. д.).
- `**type**`: Используется для определения типа данных в GraphQL. `**type**` может содержать набор полей, каждое из которых имеет свой собственный тип. Например, `**UserDto**` является типом с полями `**avatarLocation**`, `**confirmationDate**`, `**creationDate**` и др., каждое из которых имеет свой собственный тип данных (String, LocalDateTime и т. д.).

С точки зрения GraphQL, `**input**`, `**enum**` и `**type**` - это всего лишь способы определения структуры данных.

```GraphQL
# This file was generated. Do not edit manually.

schema {
    query: Query
    mutation: Mutation
}

directive @javaType(name: String!) on SCALAR

type CommentHomeWorkDto {
    content: String
    creationDate: LocalDateTime
    creator: UserDto
    homeWork: StudentHomeWorkDto
    id: ID
}

type CommentHomeWorksDto {
    items: [CommentHomeWorkDto]
    limit: Int
    offset: Int
    totalElements: Long
}

type ContentFileDto {
    fileLocation: String
    id: ID
    name: String
    size: Long
    type: String
}

type LectureContentDto {
    type: String
    url: String
    value: String
}

type LectureContentHomeWorkDto {
    type: String
    url: String
    value: String
}

type LectureDto {
    creationDate: LocalDateTime
    description: [String]
    homeWorkLevel: LectureHomeWorkLevelDto
    id: ID
    modificationDate: LocalDateTime
    speakers: [UserDto]
    subject: String
}

type LectureHomeWorkLevelDto {
    code: String
    description: String
    estimate: Int
    id: ID
}

type LectureInfoDto {
    content: [LectureContentDto]
    contentHomeWork: [LectureContentHomeWorkDto]
    creationDate: LocalDateTime
    description: [String]
    homeWorkLevel: LectureHomeWorkLevelDto
    id: ID
    modificationDate: LocalDateTime
    speakers: [UserDto]
    subject: String
}

type LectureInfoShortDto {
    content: [LectureContentDto]
    creationDate: LocalDateTime
    description: [String]
    homeWorkLevel: LectureHomeWorkLevelDto
    id: ID
    modificationDate: LocalDateTime
    speakers: [UserDto]
    subject: String
}

type LecturesDto {
    items: [LectureDto]
    limit: Int
    offset: Int
    totalElements: Long
}

"Mutation root"
type Mutation {
    approved(homeWorkId: ID!): StudentHomeWorkDto
    changePassword(newPassword: String!, oldPassword: String!): Void
    changePasswordByUserId(password: String!, userId: ID!): Void
    "user section"
    createUser(input: UserCreateInput!): UserDto
    deleteComment(id: ID!): Void
    deleteHomeWork(id: ID!): Void
    deleteLecture(id: ID!): Void
    deleteLectureHomeWorkLevel(id: ID!): Void
    deleteTraining(id: ID!): Void
    deleteTrainingTariff(id: ID!): Void
    lockUser(id: ID!): Void
    notApproved(homeWorkId: ID!): StudentHomeWorkDto
    resetState(homeWorkId: ID!): StudentHomeWorkDto
    "commentHomeWork section"
    sendComment(content: String!, homeWorkId: ID!): CommentHomeWorkDto
    "studentHomeWork section"
    sendHomeWorkToCheck(content: String!, lectureId: ID!): StudentHomeWorkDto
    takeForReview(homeWorkId: ID!): StudentHomeWorkDto
    unlockUser(id: ID!): Void
    updateComment(content: String!, id: ID!): CommentHomeWorkDto
    updateHomeWork(content: String!, id: ID!): StudentHomeWorkDto
    "lecture section"
    updateLecture(input: LectureInput!): LectureInfoDto
    updateLectureHomeWorkLevel(input: LectureHomeWorkLevelInput!): LectureHomeWorkLevelDto
    updateRole(id: ID!, roles: [UserRole]): UserDto
    "training section"
    updateTraining(input: TrainingInput!): TrainingDto
    "training lecture"
    updateTrainingLecture(id: ID!, lectureIds: [ID!]): [TrainingLectureDto]
    "training purchase section"
    updateTrainingPurchase(input: TrainingPurchaseInput!): TrainingPurchaseDto
    "training tariff"
    updateTrainingTariff(input: TrainingTariffInput!): TrainingTariffDto
    updateUser(input: UserUpdateInput!): UserDto
}

"Query root"
type Query {
    commentsHomeWorkByHomeWork(homeWorkId: ID!, limit: Int!, offset: Int!, sort: CommentHomeWorkSort): CommentHomeWorksDto
    "commentHomeWork section"
    commentsHomeWorkById(id: ID!): CommentHomeWorksDto
    "studentHomeWork section"
    homeWork(id: ID!): StudentHomeWorkDto
    homeWorkByLecture(lectureId: ID!): StudentHomeWorkDto
    homeWorkByStudentAndLecture(lectureId: ID!, studentId: ID!): StudentHomeWorkDto
    homeWorks(filter: StudentHomeWorkFilter, limit: Int!, offset: Int!, sort: StudentHomeWorkSort): StudentHomeWorksDto
    homeWorksByLectureId(lectureId: ID!, limit: Int!, offset: Int!, sort: StudentHomeWorkSort): StudentHomeWorksDto
    homeWorksByStatus(limit: Int!, offset: Int!, sort: StudentHomeWorkSort, status: StudentHomeWorkStatus!): StudentHomeWorksDto
    "lecture section"
    lecture(id: ID): LectureInfoShortDto
    lectureHomeWork(lectureId: ID): [LectureContentHomeWorkDto]
    lectureHomeWorkLevel(id: ID): LectureHomeWorkLevelDto
    lectureHomeWorkLevels: [LectureHomeWorkLevelDto]
    lectures(limit: Int!, offset: Int!, sort: LectureSort): LecturesDto
    lecturesByMentor(limit: Int!, offset: Int!, sort: LectureSort): LecturesDto
    mentors(limit: Int!, offset: Int!, sort: UserSort): UsersDto
    "training section"
    training(id: ID!): TrainingDto
    "training lecture"
    trainingLectures(id: ID!): [TrainingLectureDto]
    "purchase section"
    trainingPurchases: [TrainingPurchaseDto]
    trainingPurchasesByUserId(userId: ID!): [TrainingPurchaseDto]
    "training tariff"
    trainingTariffs(limit: Int!, offset: Int!, sort: TrainingTariffSort): TrainingTariffsDto
    trainings(limit: Int!, offset: Int!, sort: TrainingSort): TrainingsDto
    trainingsByMentor(limit: Int!, offset: Int!, sort: TrainingSort): TrainingsDto
    "user section"
    user: UserDto
    userRoles: [UserRoleDto]
    users(limit: Int!, offset: Int!, sort: UserSort): UsersDto
}

type StudentHomeWorkDto {
    answer: String
    creationDate: LocalDateTime
    endCheckingDate: LocalDateTime
    id: ID
    lecture: LectureInfoDto
    mentor: UserDto
    startCheckingDate: LocalDateTime
    status: StudentHomeWorkStatus
    student: UserDto
}

type StudentHomeWorksDto {
    items: [StudentHomeWorkDto]
    limit: Int
    offset: Int
    totalElements: Long
}

type TrainingDto {
    content: String
    id: ID!
    mentors: [UserDto]
    name: String!
    tariffs: [TrainingTariffDto]
    techStack: TechStack!
}

type TrainingLectureDto {
    id: ID
    lastLecture: LectureDto
    lecture: LectureDto
    locking: Boolean
    number: Int
}

type TrainingPurchaseDto {
    id: ID
    trainingTariff: TrainingTariffDto!
    user: UserDto!
}

type TrainingTariffDto {
    code: String
    description: String
    homeWork: Boolean
    id: ID
    name: String
    price: Float
    training: TrainingDto
}

type TrainingTariffsDto {
    items: [TrainingTariffDto]
    limit: Int
    offset: Int
    totalElements: Long
}

type TrainingsDto {
    items: [TrainingDto]
    limit: Int
    offset: Int
    totalElements: Long
}

type UserDto {
    avatarLocation: String
    confirmationDate: LocalDateTime
    creationDate: LocalDateTime
    email: String
    firstName: String
    id: ID
    lastName: String
    locked: Boolean
    middleName: String
    phoneNumber: String
    roles: [UserRole]
    updateDate: LocalDateTime
}

type UserRoleDto {
    description: String
    name: String
}

type UsersDto {
    items: [UserDto]
    limit: Int
    offset: Int
    totalElements: Long
}

enum CommentHomeWorkSortField {
    CREATION_DATE
    CREATOR
}

enum LectureSortField {
    CREATION_DATE
    SUBJECT
}

enum Order {
    ASC
    DESC
}

enum StudentHomeWorkSortField {
    CREATION_DATE
    END_CHECKING_DATE
    MENTOR
    START_CHECKING_DATE
    STATE
    STUDENT
}

enum StudentHomeWorkStatus {
    APPROVED
    IN_REVIEW
    NEW
    NOT_APPROVED
}

enum TechStack {
    JAVA
    PYTHON
}

enum TrainingSortField {
    CREATION_DATE
    NAME
}

enum TrainingTariffField {
    CODE
    CREATION_DATE
    NAME
}

enum UserRole {
    ADMIN
    LECTOR
    MANAGER
    MASTER
    MENTOR
    STUDENT
}

enum UserSortField {
    EMAIL
    LAST_NAME
    PHONE
}

"An arbitrary precision signed decimal"
scalar BigDecimal

"An arbitrary precision signed integer"
scalar BigInteger

"An RFC-3339 compliant Full Date Scalar"
scalar Date

"An RFC-3339 compliant DateTime Scalar"
scalar DateTime

"A local datetime string in 'full-date\"T\"partial-time' format RFC3339"
scalar LocalDateTime

"A local time string in 24-hr HH:mm[:ss[.SSS]] format"
scalar LocalTime

"A 64-bit signed integer"
scalar Long

"An RFC-3339 compliant Full Time Scalar"
scalar Time

"A number of milliseconds from start of UNIX epoch"
scalar Timestamp

"A Url scalar"
scalar Url

"Void"
scalar Void

input CommentHomeWorkSort {
    field: CommentHomeWorkSortField
    order: Order
}

input LectureContentHomeWorkInput {
    type: String
    url: String
    value: String
}

input LectureContentInput {
    type: String
    url: String
    value: String
}

input LectureHomeWorkLevelInput {
    code: String
    description: String
    estimate: Int
    id: ID
}

input LectureInput {
    content: [LectureContentInput]
    contentHomeWork: [LectureContentHomeWorkInput]
    description: [String]
    homeWorkLevelCode: String
    id: ID
    speakers: [String]
    subject: String
}

input LectureSort {
    field: LectureSortField
    order: Order
}

input StudentHomeWorkFilter {
    creationDateFrom: LocalDateTime
    creationDateTo: LocalDateTime
    lectureId: ID
    mentorId: ID
    status: StudentHomeWorkStatus
    trainingId: ID
}

input StudentHomeWorkSort {
    field: StudentHomeWorkSortField
    order: Order
}

input TrainingInput {
    content: String
    id: ID
    mentors: [String]
    name: String
    techStack: TechStack!
}

input TrainingLectureInput {
    lastLecture: ID
    lecture: ID!
    locking: Boolean
}

input TrainingPurchaseInput {
    id: ID
    trainingTariffCode: String
    userEmail: String
}

input TrainingSort {
    field: TrainingSortField
    order: Order
}

input TrainingTariffInput {
    code: String
    description: String
    homeWork: Boolean
    id: ID
    name: String
    price: Float
    trainingName: String
}

input TrainingTariffSort {
    field: TrainingTariffField
    order: Order
}

input UserCreateInput {
    email: String!
    firstName: String!
    id: ID
    lastName: String!
    middleName: String
    password: String!
    phoneNumber: String
}

input UserSort {
    field: UserSortField
    order: Order
}

input UserUpdateInput {
    email: String!
    firstName: String!
    id: ID
    lastName: String!
    middleName: String
    phoneNumber: String
}
```
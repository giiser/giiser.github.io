# giiser.github.io

# Learning App project
- Contentful CMS
- Java Backend
- iOS App
- MVP2: Web App

# Contentful Content Schema
## Subject (Top Level)
| Field Name    | Type             | Required | Notes                         |
| ------------- | ---------------- | -------- | ----------------------------- |
| `title`       | Short text       | ✅        | e.g. “Java Fundamentals”      |
| `slug`        | Short text       | ✅        | unique, URL-safe              |
| `description` | Short text       | ❌        | short intro                   |
| `icon`        | Media (image)    | ❌        | SF Symbols name also possible |
| `themeColor`  | Short text       | ❌        | HEX color (e.g. `#5B7CFA`)    |
| `order`       | Number (integer) | ❌        | sorting in app                |
| `isPublished` | Boolean          | ✅        | control visibility            |

## Topic
| Field Name    | Type                | Required | Notes                    |
| ------------- | ------------------- | -------- | ------------------------ |
| `title`       | Short text          | ✅        | e.g. “Variables & Types” |
| `slug`        | Short text          | ✅        | unique per subject       |
| `subject`     | Reference → Subject | ✅        | parent                   |
| `description` | Short text          | ❌        | shown before lessons     |
| `order`       | Number              | ❌        | sorting                  |
| `isPublished` | Boolean             | ✅        | hide drafts              |

## Lesson
| Field Name      | Type              | Required | Notes            |
| --------------- | ----------------- | -------- | ---------------- |
| `title`         | Short text        | ✅        | lesson name      |
| `slug`          | Short text        | ✅        | unique           |
| `topic`         | Reference → Topic | ✅        | parent           |
| `summary`       | Short text        | ❌        | preview text     |
| `content`       | Rich text         | ✅        | main lesson body |
| `order`         | Number            | ❌        | lesson order     |
| `coverImage`    | Media             | ❌        | optional         |
| `isPublished`   | Boolean           | ✅        | visibility       |

## Quiz
| Field Name     | Type               | Required | Notes                   |
| -------------- | ------------------ | -------- | ----------------------- |
| `lesson`       | Reference → Lesson | ✅        | parent                  |
| `question`     | Short text         | ✅        | question text           |
| `options`      | Short text (list)  | ✅        | answers                 |
| `correctIndex` | Number             | ✅        | index of correct option |
| `explanation`  | Short text         | ❌        | shown after answer      |
| `order`        | Number             | ❌        | ordering                |
| `isPublished`  | Boolean            | ✅        | hide drafts             |

### Relationship overview
Subject
 └── Topic
      └── Lesson
           └── Quiz (1..n)

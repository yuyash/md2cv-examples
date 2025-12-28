<!--
This CV uses environment variables instead of frontmatter for personal information.
md2cv reads the following environment variables directly:

Required GitHub Secrets:
- CV_EN_NAME
- CV_EN_EMAIL_ADDRESS
- CV_EN_PHONE_NUMBER
- CV_EN_HOME_ADDRESS
- CV_EN_LINKEDIN

For local development:
md2cv automatically loads .env file from the same directory as the markdown file.
1. Copy .env.example to .env
2. Fill in your information
3. Run: npx md2cv -i cv-en-env-variables/cv-en.md -o cv-en-env-variables/cv-en -f cv -t both -p a4

For GitHub Actions:
1. Go to Settings > Secrets and variables > Actions
2. Add the secrets listed above with your personal information
-->

# Summary

Experienced software engineer with 5+ years in full-stack development. Passionate about building scalable systems and mentoring teams. Proven track record of delivering high-impact projects and driving technical excellence.

# Core Competencies

```resume:competencies
- header: Technical Leadership
  description: Led cross-functional teams of 5-10 engineers, driving architecture decisions and establishing best practices for code quality and testing.
- header: System Design
  description: Designed and implemented microservices architecture handling 1M+ daily active users with 99.9% uptime.
- header: Agile Development
  description: Champion of agile methodologies, facilitating sprint planning, retrospectives, and continuous improvement initiatives.
```

# Experience

```resume:experience
- company: Tech Corp
  location: San Francisco, CA
  roles:
    - title: Senior Software Engineer
      start: 2021-01
      end: present
      summary:
        - Lead engineer for the platform team, responsible for core infrastructure and developer experience.
      highlights:
        - Led development of microservices architecture serving 1M+ users
        - Mentored junior developers and conducted code reviews
        - Improved system performance by 40% through optimization
- company: StartupXYZ
  location: San Francisco, CA
  roles:
    - title: Software Engineer
      start: 2019-03
      end: 2020-12
      highlights:
        - Built React-based frontend applications
        - Implemented RESTful APIs with Node.js
        - Collaborated with product team on feature development
```

# Education

```resume:education
- school: Stanford University
  degree: Bachelor of Science in Computer Science
  location: Stanford, CA
  start: 2015-09
  end: 2019-06
  details:
    - GPA 3.8/4.0
    - Dean's List
```

# Skills

- JavaScript
- TypeScript
- Python
- Go
- React
- Vue.js
- Node.js
- PostgreSQL
- Redis
- AWS
- Docker
- Kubernetes

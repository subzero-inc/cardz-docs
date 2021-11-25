
# Cardz Technical Architecture
**The following information may be of use to those interested in the underlying technological stack beneath Cardz services.** 

As a normal end-user, you don't need any of the information on this page.

## Frontend
Our frontend is a single page app written in Svelte that communicates with the server over a REST API.

This is built, then served through Netlify and Cloudflare.

## Backend services
The Cardz backend is a monolithic service that is responsible for providing the following services:

- Flashcard generation, which involves:
    - Creation of a GPT-3 prompt
    - Requesting completions through the OpenAI API
    - Parsing the completion and updating the central database
- User authentication, which involves:
    - Ensuring session credentials are up to date
    - Limiting access to resources based on session information as well as user privileges
    - Dynamically updating user privileges based on external data - for example, Stripe webhooks and/or moderation requests
- Flashcard management services, which involve:
    - Creating, reading, updating and deleting flashcards on user requests (`CRUD`)


## Backend architecture
We use [Hashicorp Terraform](https://terraform.io/) to provision services globally in order to ensure that our architecture is stable across regions. Our services are deployed on Google Cloud.

## Email services
Cardz provides email subscriptions to some users. These are managed by our email services architecture.

Each new subscription runs on its individual serverless Cloud Run service, which is triggered by a chron job. It uses Amazon SES to send emails.

The service must read from a primary database to get the list of users that are subscribed to the email that is to be sent.

Each service is also responsible for keeping track of each, individual email it sends in the primary `emails` database, and issuing unsubscribe tokens, which can be used to unsubscribe from the email.

These allow us to track email unsubscribe rates, which is important information for user retention (as well as more mundane uses, like checking whether a user even got the email that they're trying to unsubscribe from).

It is a primary goal of the email service(s) to not spam users who do not want emails, because this eventually leads to the reporting of our emails as spam, which can lead to our SES account being closed. Therefore, we provide ample opportunity to unsubscribe both from the email itself and the primary user interface.
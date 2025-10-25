🕒 ***What is @Lazy in Spring Boot?***

By default, Spring initializes all singleton beans eagerly — meaning as soon as the application context starts, Spring creates all the beans (even if they’re never used yet).

***@Lazy tells Spring***:

“Don’t create this bean when the application starts — create it only when it’s first requested or used.”

🚀 ***Benefits of @Lazy***

✅ Faster startup time (useful for large applications)
✅ Avoid circular dependency issues in some cases
✅ Load resources only when needed (memory efficiency)
---
name: Laravel Basics
description: Fundamental architectural rules and patterns for Laravel.
---

# Laravel Basics Skill

## Architecture (3-Tier)
1. **Controllers**: Handle HTTP requests and return responses. Keep them thin.
2. **Services**: Contain business logic. Decouple logic from the controller.
3. **Models (Eloquent)**: Handle database interaction and relationships.

## Best Practices
- Use **Form Requests** for validation.
- Use **Resource Classes** for API transformations.
- Ensure **CSRF Protection** is enabled on all POST/PUT/DELETE forms.

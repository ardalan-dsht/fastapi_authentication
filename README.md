

# Fastapi Authentication
This module provides a straightforward implementation of OAuth2 authentication for your FastAPI application, utilizing MongoDB for user authentication and employing tokens for endpoint access.

You may choose to utilize either a .env file as demonstrated in the example or opt for a Docker Compose file, wherein you can specify the environment variables directly within that file.

```text
MONGO_USER_USERNAME=username
MONGO_USER_PASSWORD=password
MONGO_USER_HOST=localhost
MONGO_USER_PORT=27017
MONGO_USER_DBNAME=authentication
MONGO_USER_COLLECTION=users
SECRET_KEY=your-secret-key
ALGORITHM=HS256
```

This is a simple example on how you can use this module.  
The current_user arg is the authenticated user schema which is stored in schemas.py .
```python
from fastapi_authentication import User, get_current_active_user


@router.get("/my_endpoint", tags=["MyCustomModule"])
async def my_endpoint(current_user: User = Depends(get_current_active_user)):
    """
    Docstring for OpenAPI documentation ...
    """
    return "This is awesome!"
```

In order to add users to the database you can use the compass app.  
This is how you can generate hashed passwords

```python
from fastapi_authentication import get_password_hash

hashed_password = get_password_hash(plain_text_password)
```

# Throw and Handle Error

## Throw managed error

name: it should be a string that can be used to get the human readable text from a message library. It should be unique in the whole platform and can be used to identify in the script (e.g by "if" or "switch case" statements) 

detail: it should be a JSON object, it can contain any content that helps to explain the error or provide more helpful info

### throw
```javascript
    //_.throw(name, detail);
    _.throw('ERROR_API_EMAIL_TITLE_NOT_DEFINED',{statusCode: 400, sender, receipient, title, template});
```

### return with error
```javascript
    /*
    _.onError(error, settings)
    settings is a object {name, detail, callback} 

    use correct HTTP error defiled in the constant.js
    export const HTTPERROR_400 = { statusCode: 400, statusName: 'Bad Request' };
    export const HTTPERROR_401 = { statusCode: 401, statusName: 'Unauthorized' };
    export const HTTPERROR_402 = { statusCode: 402, statusName: 'Payment Required' };
    export const HTTPERROR_403 = { statusCode: 403, statusName: 'Forbidden' };
    export const HTTPERROR_404 = { statusCode: 404, statusName: 'Not Found' };
    export const HTTPERROR_405 = { statusCode: 405, statusName: 'Method Not Allowed' };
    export const HTTPERROR_406 = { statusCode: 405, statusName: 'Not Acceptable' };
    export const HTTPERROR_407 = { statusCode: 407, statusName: 'Proxy Authentication Required' };
    export const HTTPERROR_408 = { statusCode: 408, statusName: 'Request Timeout' };
    export const HTTPERROR_429 = { statusCode: 429, statusName: 'Too Many Requests' };
    export const HTTPERROR_500 = { statusCode: 500, statusName: 'Internal Server Error' };
    export const HTTPERROR_501 = { statusCode: 501, statusName: 'Not Implemented' };
    export const HTTPERROR_502 = { statusCode: 502, statusName: 'Bad Gateway' };
    export const HTTPERROR_503 = { statusCode: 503, statusName: 'Service Unavailable' };
    export const HTTPERROR_504 = { statusCode: 504, statusName: 'Gateway Timeout' };
    */

    return _.onError(HTTPERROR_400, {
        name: 'ERROR_API_MISSING_PARAMETERS', 
        detail: { paramName: 'id' }
    });
```

## Throw differet type of errors

### Missing parameter
```javascript
    return _.onError(HTTPERROR_400, { 
        name: 'ERROR_API_MISSING_PARAMETERS',
        detail: {paramName: 'id'}
    });
```

### Permission Denied
```javascript
    return _.onError(HTTPERROR_403, { 
        name: 'ERROR_API_PERMISSION_DENIED',
        detail: {
            message: 'The operation requires Root-Admin role.',
            //other variable values that help explain further
        }
    });
```

### Catch and return exception
```javascript
    catch(error)
    {
        return _.onError(error, { 
            name: 'ERROR_API_SOMENAME',
            event, 
            detail: {
                //other variable values that help explain further
            }
        });
    }
```
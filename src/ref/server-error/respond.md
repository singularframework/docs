## respond(res)

**Type:** Function  
**Arguments:**
  - res  
    **Type:** [Response](../middleware-parameters/response)  
    **Required:** Yes  
    **Description:** A middleware [Response](../middleware-parameters/response) object.

**Returns:** void  
**Description:** Responds to a server request using a [Response](../middleware-parameters/response) object while setting the HTTP status code from [httpCode](#httpcode) and setting the body as a JSON object with the following properties:
  - **error**: from [error](#error)
  - **message**: from [message](#message)
  - **code**: from [code](#code)

```ts
import { Request, Response } from '@steroids/core';

function routeHandler(req: Request, res: Response) {

  new ServerError('Something went wrong!', 500, 'unknown')
  .respond(res);
  /** HTTP STATUS: 500
  *   BODY:
  *   {
  *     error: true,
  *     message: 'Something went wrong!',
  *     code: 'unknown'
  *   }
  **/

}
```

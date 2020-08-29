# Middleware Parameters

The following parameters are available to all [middleware/route handlers](../router-decorator/routedefinition/#handler) of routers:
  - req  
    **Type:** [Request](./request)  
    **Description:** The request object.
  - res  
    **Type:** [Response](./response)  
    **Description:** The response object.
  - next  
    **Type:** [NextFunction](./nextfunction)  
    **Description:** A function to call for moving on to the next middleware in the stack (if any).

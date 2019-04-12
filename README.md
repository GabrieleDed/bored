# Bored api
- [x] Replace "WEB system" with your system name

## Description

A system which asks the user if he wishes to provide information about the activities that will be generated or let the system generate them randomly. If user provides the information the list of activities will be generated by the user choices. Otherwise the list will be generated randomly. Generated list of activities provides a user with a wide range to choose from. After Choosing the one user wishes, the system provides the users with a certain information about the activity. 

- [x] Provide WEB system description in few sentences - its purpose, users, etc.

## Entity definition
- [ ] Define the entity ("object" that will be manipulated) of WEB system
- [x] Entity should have a name

Name of entity - Activity

- [ ] Entity should have 3 mandatory attributes:
    - [x] ID - depending on specific service this could be a number or string
    "Key" - specific and unique set of numbers [1000000, 9999999]
    - [ ] Creation date - (if applicable for specific service) ISO 8601 format date string
    - [ ] Modification date - (if applicable for specific service) ISO 8601 format date string
- [ ] Entity should have at least 5 custom attributes
    - [x] Each attribute should have a type defined: number, string, ISO 8601 date string, boolean, object, array or other
    - [x] Each attribute should have restrictions defined: list of constants, or number range, or string length, or string format, or object schema, or array schema or other. For example, you can use `joi` language to define restrictions: 
    'Activity' - Description of the queried activity
    'Accessibility' - A factor describing how possible an event is to do with zero being the most accessible [0.0, 1.0]
    'Type' - Type of the activity ["education", "recreational", "social", "diy", "charity", "cooking", "relaxation", "music", "busywork"]
    'Participants' - The number of people that this activity could involve[0, n]
    'Price' - A factor describing the cost of the event with zero being free [0, 1]
    'Key' - A unique numeric id [1000000, 9999999]
    https://github.com/hapijs/joi/blob/v13.1.2/API.md

## API definition
- [ ] Define specific service (konkrečios paslaugos) API methods that WEB system is going to use
- [ ] Optionally define additional API methods that WEB system is going to expose
- [ ] API should have at least 4 methods
    - [ ] A method to return entity by ID. Should not have request body
    
    GET - /api/activity/
        - Gets random activity (http://www.boredapi.com/api/activity)
   
    
    - [ ] A method to return multiple entities (Array) by ID. This method should support at least one header value to:
        - [ ] Return only entities that match pattern in one of its attributes
        
        Get - /api/activity?key=:key
            Gets a specific activity by th key vlue(http://www.boredapi.com/api/activity?key=5881028)
        - [ ] Return 10 entities starting provided index
        - [ ] Return sorted entities by one of its attributes (both ascending and descending)
        - [ ] Other (should be approved by Product Owner (PO))
    - [ ] A method to remove entity by ID. Returns removed entity. Should not have request body
            DELETE /api/activity/{id}
    - [ ] A method to update entity by ID. Accepts entity to update and returns updated entity
- [ ] Each method should have HTTP method defined
- [ ] Each method should have URI defined (use {id} as entity ID placeholder)
- [ ] Should return all 4xx errors in unified format. Define format using `joi` language
- [ ] Should return all 5xx errors in unified format. Define format using `joi` language

## UI definition
- [ ] Define the structure of how visually the WEB system is going to look like
- [ ] Should have at least one view defined with https://wireframe.cc (or other wireframe tool):
- [ ] The view should have a title
- [ ] The view should have a description of a service provided by web system
- [ ] The view should include at least 2 UI components:
    - [ ] A component to display multiple entities with all their attribute values visible. It should be posible to remove and edit selected entity.
        - [ ] Depending on chosen header of API method that returns multiple entities, it should be posible to select specific 10 entities starting index, sort entities by attribute, filter entities by attribute pattern, or other (should be approved by Product Owner (PO))
    - [ ] A component to create a new entity/edit existing entity. It should be posbile to create new entity and edit selected entity
        - [ ] Each attribute should have a dedicated editor field: text box for string or number, checkbox or radio buttons for boolean, date picker for date, etc.

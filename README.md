Pet Management API Documentation
Base URL: /pet
Endpoints
1. Add Pet
Creates a new pet record.
URL: /add-pet
Method: POST
Content-Type: application/json
Request Body:
{
    "petId": “Long”,
    "petName": "String",
    "age": “Integer”,
    "gender": "String",
    "remarks": "String",
    "petType": "String",
    "ownerId": "String”
}

Success Response:
Code: 200
Content: "Pet added successfully"
Error Response:
Code: 400 BAD REQUEST
Content: Map of field validation errors

{
"fieldName": "error message"
}




2. Get All Pets
 Retrieves all pet records.
URL: /pet-get-all
Method: GET
Success Response:
Code: 200
Content: Array of pet objects
[
{
    "petId": “Long”,
    "petName": "String",
    "age": “Integer”,
    "gender": "String",
    "remarks": "String",
    "petType": "String",
    "ownerId": "String”
}
]

3. Search pet by ID
 Retrieves a specific pet by their ID.
URL: /pet-search-by-id/{id}
Method: GET
URL Parameters: id=[long]
Success Response:
Code: 200
Content: Pet object

4. Search Pets by Name
 Retrieves pets matching the provided name.
URL: /pet-search-by-name/{name}
Method: GET
URL Parameters: name=[string]
Success Response:
Code: 200
Content: Array of matching pet objects
5. Update Pet
 Updates an existing pet record.
tent-Type: application/json
Request Body: Pet object
Success Response:
Code: 200
Content: "Pet updated successfully"
Error Response:
Code: 400 BAD REQUEST
Content: Map of field validation errors

6. Delete Pet by ID
 Deletes a specific pet record.
URL: /pet-delete-by-id/{id}
Method: DELETE
URL Parameters: id=[long]
Success Response:
Code: 200
Content: "pet deleted successfully"

7. Delete All Pets
 Deletes all pet records.
URL: /pet-delete-all
Method: DELETE
Success Response:
Code: 200
Content: "All pets deleted successfully"




Error Handling
The API includes global error handling for validation errors. When validation fails:
Code: 400 BAD REQUEST
Content: JSON object mapping field names to error messages
{
"fieldName": "validation error message"
}
Cross-Origin Resource Sharing (CORS)
This API supports CORS and can be accessed from different origins.
Notes
All endpoints requiring an ID or performing modifications include validation
Response formats are consistently JSON
Successful operations return appropriate success messages
Error responses include specific validation messages for easy debugging


Example Usage
JavaScript/Fetch API Example

// Adding a new pet
const response = await fetch('http://[your-domain]/pet/add-pet', {
  method: 'POST',
  headers: {
      'Content-Type': 'application/json',
  },
  body: JSON.stringify({
      name: 'Max',
      // Other pet properties
  })
});


if (!response.ok) {
  const errorData = await response.json();
  // Handle validation errors
  console.error('Validation errors:', errorData);
}

## Question
Imagine a sophisticated hierarchical data structure in JavaScript that models an organization's intricacies, encompassing details such as employee ID, name, position, department, and subordinates. Your task is to design a function, `getEmployeesByPosition(organization, position)` ( starting code is provided below ),  which takes this organizational data structure as input along with a position ( e.g “Software Engineer” ) and efficiently produces an array containing information about all employees holding the given position within the organization. Your implementation should seamlessly navigate the complexity of the hierarchical data and deliver a clear and concise result. Either use [JSPlayground](https://www.jsplayground.dev) as your environment or any online editor that you're comfortable with.

## Organization object:
```js
const organization = {
  id: 1,
  name: "Company",
  type: "Organization",
  employees: [
    {
      id: 2,
      name: "John Doe",
      position: "Manager",
      department: "Operations",
      subordinates: [
        {
          id: 3,
          name: "Alice Smith",
          position: "Team Lead",
          department: "Operations",
          subordinates: [],
        },
        {
          id: 4,
          name: "Bob Johnson",
          position: "Senior Developer",
          department: "Engineering",
          subordinates: [
            {
              id: 5,
              name: "Charlie Brown",
              position: "Software Engineer",
              department: "Engineering",
              subordinates: [
                {
                  id: 14,
                  name: "Jason Clive",
                  position: "Software Engineer",
                  department: "Engineering",
                  subordinates: [],
                },
              ],
            },
          ],
        },
      ],
    },
    {
      id: 6,
      name: "Jane Miller",
      position: "Software Engineer",
      department: "Human Resources",
      subordinates: [],
    },
  ],
};
```

## Starting code
```js
/**
 * Retrieves an array containing information about all employees holding the 
 * given position within the organization's hierarchical data structure.
 *
 * @param {Object} organization - The hierarchical data structure representing the organization.
 * @param {string} position - The position for which employees' information is to be 
 *                            retrieved (e.g., "Software Engineer").
 * @returns {Array<Object>} - An array containing information about employees holding the specified position.
 *   Each element in the array is an object with properties like employee ID, name, position, and department.
 *   The array is structured to navigate through the organizational hierarchy.
 */
function getEmployeesByPosition(organization, position) {
  // ...your code...

const result = [];

  function traverse(employees) {
    for (const emp of employees) {
      // Check current employee
      if (emp.position === position) {
        result.push({
          id: emp.id,
          name: emp.name,
          position: emp.position,
          department: emp.department,
        });
      }

      // Traverse subordinates recursively
      if (emp.subordinates && emp.subordinates.length > 0) {
        traverse(emp.subordinates);
      }
    }
  }

  // Start traversal from top-level employees
  traverse(organization.employees);

  return result;
}
```

# Lab_Act4

This lab focuses on the exploration and implementation of various SQL JOIN operations in a database, aiming to retrieve related data from multiple tables. Here’s a step-by-step breakdown of what you will do:

Set up the project:

Start by copying your existing lab-auth-api folder or cloning it from GitHub to a new folder called lab-auth-joins.

Install necessary dependencies, check your environment settings, and run the server to confirm the database connection is working. The server should be accessible at http://localhost:3000/api/health
.

Extend the database:

Add new tables to the existing database, such as profiles, roles, user_roles, login_audit, and referrals. These tables will be the basis for the JOIN queries.

The profiles table will be a one-to-one relationship with the users, while roles and user_roles will form a many-to-many relationship.

The login_audit table will track sign-ins, and the referrals table will be used for self-join exploration.

Insert seed data:

Insert sample data into the newly created tables to ensure that there is enough data for testing the JOIN queries. Some users should have no profiles or no roles, so LEFT, RIGHT, and FULL JOIN operations can produce meaningful NULL values.

Write JOIN queries:

Use the newly created tables to write SQL queries utilizing different types of JOIN operations:

INNER JOIN: Fetch users with at least one role.
// // === INNER JOIN example (implement this one first) ===
// // exports.usersWithRoles = (req, res) => {
// //   const sql = `/* fill with INNER JOIN from Part 3A */`;
// //   db.query(sql, [], (err, rows) => {
// //     if (err) return res.status(500).json({ error: err.message });
// //     return res.json(rows);
// //   });
// // };

LEFT JOIN: Retrieve all users, including those with no profile.
// // === LEFT JOIN ===
// // exports.usersWithProfiles = (req, res) => {
// //   const sql = `/* fill with LEFT JOIN from Part 3B */`;
// //   db.query(sql, [], (err, rows) => {
// //     if (err) return res.status(500).json({ error: err.message });
// //     return res.json(rows);
// //   });
// // };

RIGHT JOIN: Get all roles, including those with no assigned user.
// // === RIGHT JOIN ===
// // exports.rolesRightJoin = (req, res) => {
// //   const sql = `/* fill with RIGHT JOIN from Part 3C */`;
// //   db.query(sql, [], (err, rows) => {
// //     if (err) return res.status(500).json({ error: err.message });
// //     return res.json(rows);
// //   });
// // };

FULL OUTER JOIN: Emulate it using a combination of LEFT JOIN and RIGHT JOIN to get all profiles and users, even those without matches.
// // === FULL OUTER (UNION) ===
// // exports.profilesFullOuter = (req, res) => {
// //   const sql = `/* fill with UNION of LEFT + RIGHT from Part 3D */`;
// //   db.query(sql, [], (err, rows) => {
// //     if (err) return res.status(500).json({ error: err.message });
// //     return res.json(rows);
// //   });
// // };

CROSS JOIN: List every possible combination of users and roles.
// // === CROSS JOIN ===
/* // exports.userRoleCombos = (req, res) => {
     const sql = `/* fill with CROSS JOIN from Part 3E */`;
     db.query(sql, [], (err, rows) => {
       if (err) return res.status(500).json({ error: err.message });
       return res.json(rows);
     });
   };
*/

SELF JOIN: Explore the referrals table to find out who referred whom among users.
// // === SELF JOIN (referrals) ===
// // exports.referrals = (req, res) => {
// //   const sql = `/* fill with SELF JOIN from Part 3F */`;
// //   db.query(sql, [], (err, rows) => {
// //     if (err) return res.status(500).json({ error: err.message });
// //     return res.json(rows);
// //   });
// // };

// // === Latest login per user ===
// // exports.latestLogin = (req, res) => {
// //   const sql = `/* fill with LEFT JOIN + subquery from Part 3G */`;
// //   db.query(sql, [], (err, rows) => {
// //     if (err) return res.status(500).json({ error: err.message });
// //     return res.json(rows);
// //   });
// // };

Create protected report endpoints:

Add new routes under the /api/reports endpoint for each of the JOIN queries written in the previous step.

Implement corresponding controller functions to execute these SQL queries and return the results. Each endpoint should be protected with authentication middleware.

Test the API using Postman:

Use Postman to test each of the newly created API endpoints. Log in to obtain a JWT token and set it in the Authorization header of your requests as a Bearer Token.

Review and troubleshoot:

Verify that the API returns the anticipated data and that all JOIN operations are executed appropriately. To make sure the queries handle situations when there are no matches (like in LEFT and RIGHT JOINs), test them. Verify that no data is lost from either side of the tables to verify that the full outer join emulation is functioning. You will have a solid understanding of SQL JOIN operations and how to publish their output in a web API by the end of this lab.

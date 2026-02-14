		Assignment 3 MongoDB
		Problem Statement: MongoDB Regex
Problems

1. Write a MongoDB query to find all students whose name starts with the letter "A"
(case-insensitive).

2. Fetch all courses whose course name contains the word "data" anywhere in the
string, regardless of case.

3. Find all users whose email ends with @gmail.com.

4. Display employees whose city name contains the first letter as ‘C’ followed by
exactly 5 characters.

5. Retrieve all contacts whose mobile number starts with 9 and contains exactly 10
digits.

6. An employees collection contains an embedded experience array with company
names.
	a. Find employees who have worked in any company whose name contains
	the word "bank" (case-insensitive).

7. Find users whose passwords contain at least one number.

8. Find products where:
	a. Product name starts with "S"
	b. Category contains the word "electronics" (case-insensitive)

9. Fetch all reviews that do NOT contain the word "bad" (case-insensitive).

10. Find all students whose roll number:
a. Starts with ‘CS’
b. Belongs to the year 2024

=============================================================================================================================================
Queries

db.hospital.find({hospitalName: /^A/i});

Output:-

{
  _id: 41,
  hospitalName: 'Apex Hospital',
  location: {
    city: 'Meerut',
    state: 'UP',
    pincode: 250001
  },
  isGovernment: false,
  establishedYear: 2005,
  rating: 4,
  departments: [
    'Ortho'
  ],
  doctors: [
    {
      doctorId: 141,
      name: 'Dr Kiran',
      specialization: 'Ortho',
      experience: 14,
      available: false
    }
  ],
  contact: {
    phone: '0121-111041',
    email: 'apex41@hosp.com'
  }
}
====================================================================================================================================================

2. db.hospital.find({hospitalName: /Hospital/i});

Output:-
{
  _id: 28,
  hospitalName: 'Pulse Hospital',
  location: {
    city: 'Mysore',
    state: 'KA',
    pincode: 570001
  },
  isGovernment: false,
  establishedYear: 2016,
  rating: 4.2,
  departments: [
    'Cardiology'
  ],
  doctors: [
    {
      doctorId: 128,
      name: 'Dr Mohit',
      specialization: 'Heart',
      experience: 9,
      available: true
    }
  ],
  contact: {
    phone: '0821-111028',
    email: 'pulse28@hosp.com'
  }
}
================================================================================================================================

3. db.hospital.find({'contact.email': /@hosp.com$/});

Output:-
{
  _id: 28,
  hospitalName: 'Pulse Hospital',
  location: {
    city: 'Mysore',
    state: 'KA',
    pincode: 570001
  },
  isGovernment: false,
  establishedYear: 2016,
  rating: 4.2,
  departments: [
    'Cardiology'
  ],
  doctors: [
    {
      doctorId: 128,
      name: 'Dr Mohit',
      specialization: 'Heart',
      experience: 9,
      available: true
    }
  ],
  contact: {
    phone: '0821-111028',
    email: 'pulse28@hosp.com'
  }
}
===================================================================================================================================================

4. db.hospital.find({'location.city': /^C.{6}$/});

Output:-
{
  _id: 9,
  hospitalName: 'Hope Care',
  location: {
    city: 'Chennai',
    state: 'TN',
    pincode: 600001
  },
  isGovernment: false,
  establishedYear: 2016,
  rating: 4.4,
  departments: [
    'Cardiology'
  ],
  doctors: [
    {
      doctorId: 109,
      name: 'Dr Meena',
      specialization: 'Heart',
      experience: 7,
      available: true
    }
  ],
  contact: {
    phone: '044-111009',
    email: 'hope9@hosp.com'
  }
}
================================================================================================================================

5. db.hospital.find({'contact.phone': /^0.{10}$/});

Output:-
{
  _id: 26,
  hospitalName: 'Fortis Care',
  location: {
    city: 'Faridabad',
    state: 'HR',
    pincode: 121001
  },
  isGovernment: false,
  establishedYear: 2004,
  rating: 4.3,
  departments: [
    'Neuro'
  ],
  doctors: [
    {
      doctorId: 126,
      name: 'Dr Manish',
      specialization: 'Neuro',
      experience: 16,
      available: false
    }
  ],
  contact: {
    phone: '0129-111026',
    email: 'fortis26@hosp.com'
  }
}
============================================================================================================================================

6. db.hospital.find({'doctors.specialization':/general/i});

Output:-
{
  _id: 47,
  hospitalName: 'Prime Care',
  location: {
    city: 'Bhubaneswar',
    state: 'OD',
    pincode: 751001
  },
  isGovernment: false,
  establishedYear: 2012,
  rating: 4.2,
  departments: [
    'General'
  ],
  doctors: [
    {
      doctorId: 147,
      name: 'Dr Ajay',
      specialization: 'General',
      experience: 11,
      available: true
    }
  ],
  contact: {
    phone: '0674-111047',
    email: 'prime47@hosp.com'
  }
}
===============================================================================================================================================

7. db.hospital.find({'contact.email': /0|1|2|3|4|5|6|7|8|9/});

Output:-
{
  _id: 28,
  hospitalName: 'Pulse Hospital',
  location: {
    city: 'Mysore',
    state: 'KA',
    pincode: 570001
  },
  isGovernment: false,
  establishedYear: 2016,
  rating: 4.2,
  departments: [
    'Cardiology'
  ],
  doctors: [
    {
      doctorId: 128,
      name: 'Dr Mohit',
      specialization: 'Heart',
      experience: 9,
      available: true
    }
  ],
  contact: {
    phone: '0821-111028',
    email: 'pulse28@hosp.com'
  }
}
============================================================================================================================================

8. a. db.hospital.find({'doctors.specialization':/^S/});

Output:-
{
  _id: 46,
  hospitalName: 'Urban Health',
  location: {
    city: 'Ahmedabad',
    state: 'GJ',
    pincode: 380001
  },
  isGovernment: false,
  establishedYear: 2016,
  rating: 4.4,
  departments: [
    'Dermatology'
  ],
  doctors: [
    {
      doctorId: 146,
      name: 'Dr Heena',
      specialization: 'Skin',
      experience: 8,
      available: true
    }
  ],
  contact: {
    phone: '079-111046',
    email: 'urban46@hosp.com'
  }
}
====================================================================================================================================

9. db.hospital.find({isGovernment: {$ne:false}})

Output:-
{
  _id: 48,
  hospitalName: 'Swasth Hospital',
  location: {
    city: 'Madurai',
    state: 'TN',
    pincode: 625001
  },
  isGovernment: true,
  establishedYear: 1993,
  rating: 3.9,
  departments: [
    'Pediatrics'
  ],
  doctors: [
    {
      doctorId: 148,
      name: 'Dr Lata',
      specialization: 'Child',
      experience: 16,
      available: true
    }
  ],
  contact: {
    phone: '0452-111048',
    email: null
  }
}
======================================================================================================================================
10. 



















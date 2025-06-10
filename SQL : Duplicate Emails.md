SELECT email as Email from Person group by email HAVING COUNT(*) > 1;

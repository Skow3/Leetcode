# EASY 

# We have to delete only one of the duplicate entries and keep the other one remaining 

Since it has been weeks practicing SQL it slipped out of my mind was trying this earlier
```SQL
DELETE from Person where email in (
  SELECT email from Person group by email having COUNT(*) >2
)
```

But this was giving error bcs it was either deleting all the entries for that duplicate but since we have to save one so ...:
```SQL
DELETE p1
FROM Person p1
JOIN Person p2
  ON p1.email = p2.email
  AND p1.id > p2.id;
```

This passed .. 

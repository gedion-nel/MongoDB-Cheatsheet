# Aggregation in MongoDB

Aggregation is the capability to combine two collections together using a single query to create a unified result set.

The following query combines the **apples** and **countries** collections. The **apples** collection is joined with the **countries** collection using the **apple.countryOfOrigin** field and the **countries.country** field as the common join fields.

## Example: Combine `apples` and `countries` Collections

### Step 1: Match the Country of Origin
The statement `{$match: { countryOfOrigin: "Mexico" }}` indicates that the query will return only those documents in which the **apples.countryOfOrigin** equals `"Mexico"`.

```javascript
{$match: { countryOfOrigin: "Mexico" }}
Step 2: Perform the Lookup (Join)
The $lookup operator is used to join the apples collection with the countries collection. It matches the countryOfOrigin field in the apples collection with the country field in the countries collection.

javascript
Copy code
{ 
  $lookup: {
    from: "countries",
    localField: "countryOfOrigin",
    foreignField: "country",
    as: "regional_info"
  }
}
Complete Query
javascript
Copy code
db.apples.aggregate([
  { $match: { countryOfOrigin: "Mexico" } },
  { 
    $lookup: {
      from: "countries",
      localField: "countryOfOrigin",
      foreignField: "country",
      as: "regional_info"
    }
  }
]).pretty()
Output: Result from Aggregation
json
Copy code
{
  "_id": ObjectId("627efc53a96c699c93564740"),
  "type": "golden delicious",
  "price": 0.99,
  "countryOfOrigin": "Mexico",
  "regional_info": [
    {
      "_id": ObjectId("627efc54bb142679f4604979"),
      "country": "Mexico",
      "continent": "North America"
    }
  ]
}
Explanation
$match: Filters the documents in the apples collection to include only those where the countryOfOrigin is "Mexico".
$lookup: Joins the apples collection with the countries collection. It finds documents in the countries collection where the country field matches the countryOfOrigin field from the apples collection.
as: The resulting joined documents from the countries collection are stored in the regional_info array.
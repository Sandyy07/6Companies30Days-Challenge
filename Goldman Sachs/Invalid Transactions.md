(Leetcode Problem)

A transaction is possibly invalid if:

the amount exceeds $1000, or;
if it occurs within (and including) 60 minutes of another transaction with the same name in a different city.
You are given an array of strings transaction where transactions[i] consists of comma-separated values representing the name, time (in minutes), amount, and city of the transaction.

Return a list of transactions that are possibly invalid. You may return the answer in any order.

 

Example 1:

Input: transactions = ["alice,20,800,mtv","alice,50,100,beijing"]
Output: ["alice,20,800,mtv","alice,50,100,beijing"]
Explanation: The first transaction is invalid because the second transaction occurs within a difference of 60 minutes, have the same name and is in a different city. Similarly the second one is invalid too.

CODE (JAVA) :

```
class Transaction {
    String name;
    int time;
    int amount;
    String city;
    boolean isValid;
    
    Transaction(String name, int time, int amount, String city) {
        this.name = name;
        this.time = time;
        this.amount = amount;
        this.city = city;
        this.isValid = true;
    }
    
    public String getString() {
        return this.name + "," +
            Integer.toString(this.time) + "," +
            Integer.toString(this.amount) + "," +
            this.city;
    }
}

class Solution {
    public List<String> invalidTransactions(String[] transactions) {
        
        List<String> output = new ArrayList<>();
        Map<String, List<Transaction>> nameToTransaction = new HashMap<>();
        
        for (String transaction : transactions) {
            String[] details = transaction.split(",");
            Transaction t = new Transaction(details[0], Integer.parseInt(details[1]), Integer.parseInt(details[2]), details[3]);
            
            if (t.amount > 1000) {
                output.add(t.getString());
                t.isValid = false;
            }
            List<Transaction> pastTransactions = nameToTransaction.getOrDefault(details[0], new ArrayList<>());
            
            for (Transaction curr : pastTransactions) {
                if (Math.abs(t.time - curr.time) <=60 && !t.city.equals(curr.city)) {                  
                    if (t.isValid){
                        output.add(t.getString());
                        t.isValid = false;
                    }
                    if (curr.isValid) {
                        output.add(curr.getString());
                        curr.isValid = false;
                    }
                } 
            }
            pastTransactions.add(t);
            nameToTransaction.put(details[0], pastTransactions);
            
        }
        
        return output;         
    }
}
```
LEETCODE ACCEPTED :
![Screenshot 2023-01-09 225450](https://user-images.githubusercontent.com/73281015/211369375-163b9ba1-164d-4945-9a77-3257ddecf302.png)


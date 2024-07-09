# Average-waiting-time
class Solution {
    public double averageWaitingTime(int[][] customers) {
         int currentTime = 0;
        long totalWaitingTime = 0;
        
        for (int[] customer : customers) {
            int arrivalTime = customer[0];
            int prepTime = customer[1];
            
            // Update current time to the maximum of current time or arrival time
            currentTime = Math.max(currentTime, arrivalTime);
            
            // Calculate waiting time for this customer
            int waitingTime = currentTime + prepTime - arrivalTime;
            
            // Update total waiting time
            totalWaitingTime += waitingTime;
            
            // Update the current time to when this order will be finished
            currentTime += prepTime;
        }
        
        // Return the average waiting time
        return (double) totalWaitingTime / customers.length;
    }
}

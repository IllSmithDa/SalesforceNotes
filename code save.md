public class CustomOrder {
    public static void updateDiscount() {
		// get all orders 
		Custom_Order__c[] customOrders = [SELECT
                                          Discount_Percent__c, 
                                          Final_Price__c, 
                                          Number_of_Units__c, 
                                          Product__r.MSRP__c,
                                          Total_Cost__c,
                                          Customer__r.Type
                                          FROM Custom_Order__c];
        for (Custom_Order__c order: customOrders) {
            system.debug(order.Customer__r.Type);
                system.debug(order.Product__r.MSRP__c);
            if(order.Customer__r.Type == 'School') {
                order.Discount_Percent__c = 10;
                
            }
            order.Total_Cost__c = (order.Final_Price__c * order.Number_of_Units__c) - ((order.Final_Price__c * order.Number_of_Units__c) * order.Discount_Percent__c);
        }
        update customOrders;
    }
}
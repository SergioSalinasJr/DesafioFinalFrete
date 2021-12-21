public with sharing class OrderItemTriggerHandler {
    List<OrderItem> oldRecords {get; set;}
    List<OrderItem> newRecords {get; set;}
    Map<Id, OrderItem> oldMap {get; set;}
    Map<Id, OrderItem> newMap {get; set;}

    public OrderItemTriggerHandler(List<OrderItem> oldRecords, List<OrderItem> newRecords, Map<Id, OrderItem> oldMap, Map<Id, OrderItem> newMap) {
        this.oldRecords = oldRecords;
        this.newRecords = newRecords;
        this.oldMap = oldMap;
        this.newMap = newMap;   
    }

    public void beforeInsert() {
        OrderItemHelper.checkOrderItem(this.newRecords);
    }

    public void afterInsert() {
        List<Order> orderList = OrderItemHelper.calculateFreight(this.newRecords);
        if(!orderList.isEmpty()) {
            update orderList;
        }
    }

    public void beforeUpdate() {
        OrderItemHelper.checkOrderItem(this.oldMap, this.newMap);
    }

    public void afterUpdate() {
        List<Order> orderList = OrderItemHelper.calculateFreight(this.oldMap, this.newMap);
        if(orderList != null && !orderList.isEmpty()) {
            update orderList;
        }
    }

    public void beforeDelete() {
        OrderItemHelper.checkOrderItem(this.oldRecords);
    }

    public void afterDelete() {
        List<Order> orderList = OrderItemHelper.calculateFreight(this.oldRecords);
        if(!orderList.isEmpty()) {
            update orderList;
        }
    }
}

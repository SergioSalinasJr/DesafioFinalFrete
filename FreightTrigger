trigger FreightTrigger on Freight__c (before insert) {
    FreightTriggerHandler handler = new FreightTriggerHandler(
        Trigger.old, Trigger.new, Trigger.newMap, Trigger.oldMap
    );

        switch on Trigger.operationType {
            when BEFORE_INSERT {
                handler.beforeInsert();
            }
        }   
}

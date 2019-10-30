# Warehouse Shuffle Problem

This was initially an assignment problem giving to me in my advanced algorithms course. Space and time complexity was a constraint. The spec is as follows.

You are in charge of storingitemsof different possibletypesin a set ofwarehouses.Each warehouse has a capacity, denoting the maximum number of items that can be stored in the warehouse,and a defined set of types of items that are able to be stored in the warehouse.  The capacity of a warehouse,and the set of types of items that can be stored in a warehouse cannot change.  At any point in time,  awarehouse keeps track of the number of each different type of item it has stored.  The total number of itemsstored in a warehouse at any point in time cannot exceed the capacity of the warehouse, and the warehousecan only store items of types that can be stored in that warehouse.  If the total number of items currentlystored in the warehouse equals the capacity of the warehouse, then we say it isfull.Atransferof one item of stock of a given typexcan be made from a source warehousesto a destinationwarehoused, if warehousescurrently contains at least one item of typex, and warehousedis not currentlyfull, and it is able to store items of typex.From time to time a new item of stock is purchased and needs to transferred from adepotto one of thewarehouses  that  you  are  in  charge  of.   (For  simplicity,  a  depot  is  a  warehouse  that  is  not  in  the  set  ofwarehouses that you are in charge of.)  If you are in charge of a warehouse that is not full that can store thetype of the new item, then this can be achieved easily by performing a single transfer of the new item ofstock from the depot, to the warehouse.  On the other hand, if all the warehouses that are able to store itemsof the given type are currently full,  then it may be necessary to first transfer items between the existingwarehouses, in order to make room for the new item, before transferring the new item from the depot toan available warehouse.  In some circumstances, there may be no way to rearrange the items in the existingwarehouses (by making transfers between them) in order to make room for the new item.Example 1For example, imagine that you are in charge of the following set of warehouses:W1 : 2 : (T8,0)W2 : 2 : (T3,0),(T6,1),(T7,1)W3 : 1 : (T1,0),(T2,1),(T9,0)W4 : 2 : (T4,1),(T6,1)W5 : 3 : (T1,1),(T3,2),(T6,0),(T8,0)W6 : 3 : (T4,0),(T8,1)W7 : 4 : (T8,4)W8 : 3 : (T2,0),(T7,0),(T8,0),(T9,3)
COMP4500/7500 Assignment 1 (August 27, 2019)4where each warehouse above is described first by its name, then its capacity, and thirdly, a list of the typesof items that can be stored in the warehouse and the number of items of that type that are currently storedin the warehouse.  E.g.  warehouseW6 has a capacity of 3 and can store items of typeT4 orT8.  It currentlystores zero items of typeT4 and one item of typeT8.If a new item of stock of typeT8 was purchased and needed to be transferred from the depotW0 : 1 : (T8,1)to one of the warehouses that you are in charge of, then this could be accomplished (easily) by performingthe following sequence of transfer operations:〈(W0, W1, T8)〉where each transfer in the list above is being represented by a tuple of the source warehouse, followed bythe destination warehouse, and then the type of the item that is transferred.  Other sequences of transfersoperations would also work, e.g.〈(W0, W6, T8)〉.Example 2If you are still in charge of the same set of warehouses (in the same initial state) from Example1, and a new item of stock of typeT1 was purchased and needed to be transferred from the depotW0 : 1 : (T1,1)to one of the warehouses that you are in charge of, then this cannot be achieved by one transfer operation,because all the warehouses that can store items of typeT1 are currently full.  The item of stock can, however,be transferred from the depot to one of the warehouses by performing the following sequence of transferoperations (in the order they are given):〈(W4, W6, T4),(W2, W4, T6),(W5, W2, T3),(W0, W5, T1)〉That  is,  an  item  of  typeT4  can  first  be  transferred  fromW4  toW6;  and  then  an  item  of  typeT6  canbe  transferred  fromW2  toW4;  then  an  item  of  typeT3  can  be  transferred  fromW5  toW2;  and  thenfinally the new item of typeT1 can be transferred from the depot,W0, to warehouseW5.  There are othersequences of valid transfer operations that would also work.Example 3If you are now in charge of the following set of warehouses (note that these differ from thosein the above examples only in the current contents ofW6);W1 : 2 : (T8,0)W2 : 2 : (T3,0),(T6,1),(T7,1)W3 : 1 : (T1,0),(T2,1),(T9,0)W4 : 2 : (T4,1),(T6,1)W5 : 3 : (T1,1),(T3,2),(T6,0),(T8,0)W6 : 3 : (T4,3),(T8,0)W7 : 4 : (T8,4)W8 : 3 : (T2,0),(T7,0),(T8,0),(T9,3)a new item of stock of typeT1 was purchased and needed to be transferred from the depotW0 : 1 : (T1,1)to  one  of  the  warehouses  that  you  are  in  charge  of,  then  this  cannot  be  done.   Not  only  are  all  of  thewarehouses that can store items of typeT1 currently full, but there is also no way to rearrange the items inthe existing warehouses (by making transfers between them) in order to make room for the new item.


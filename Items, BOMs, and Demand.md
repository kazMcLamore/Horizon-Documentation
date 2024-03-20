# Overview
The application tracks the **[Demand](#Demand)** for all of our **[[#item]]** to allow us to forecast resource availability. For this to work properly, each **[Item](#Item)** must be properly configured before it's added to a [Sales Order](Orders.md#Sales%20Orders) 

# Item
items are the basic units that can be added to [Orders](Orders.md) of all types
- "everything is an item"
- items have **types** e.g, Product, [Configurators](#Configurators), [Equipment](#Equipment), Discounts, etc. 
- each **type** has unique attributes and will generate different [Demand](#Demand) records 
- All **types** of items are [Items](#Item) and will have a record in the main item table.

![](attachments/All%20Items%20Form.png)

| attribute            | effect                                                                                                                                                    |
| -------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| consumable           | if true, will expect to make this as needed for each order                                                                                                |
| replenishment method | determines how demand records created for this product will be 'satisfied'. if set to 'purchase' then the demand will be satisfied by a 'purchase' order. |
|                      |                                                                                                                                                           |

## Configurator
- a **configurator** is a set of choices to be made by the customer for their **specific** [Sales Order](Orders.md#Sales%20Order)
	- a configurator defines the choices **to be presented** to the customer, they do NOT represent the customer's choices
	- for each choice the customer makes, **sales order items** will be created "under" the configurator 
	- choices are defined in the configurator and allow a user to select:
		- a specific number of items...
		- totaling a specific quantity...
		- from a specific category
	- categories can be created ad-hoc for any purpose.
## Equipment

- equipment is still added to the BOM.
- If on a [BOMs](#BOMs), the quantity scales but does not allow fractional quantities, always rounds up to the nearest whole unit
# BOMs
- [ ] BOM defines how to make an item from other items.
	- [ ] BOMs can include other products with BOMs.
	- [ ] BOMS can include configurators.
- [ ] an item can have many BOMs but only one **active** BOM at a time
### Demand
- [ ] a demand record represents a **quantity** of an **item** needed by a specific date/time.
- [ ] demand records have types (e.g. purchase, build, pick, etc.) that define how that demand must be **satisfied**.
- [ ] demand is generated through [Sales Orders](Orders.md#Sales%20Orders)
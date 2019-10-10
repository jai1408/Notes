## Hibernate Table Per Hierarchy

One table is required to map the inheritance hierarchy.   
Here, an extra column (also known as *discriminator* column) is created in the table to identify the class.

```
@Entity  
@Table(name = "employee101")  
@Inheritance(strategy=InheritanceType.SINGLE_TABLE)  
@DiscriminatorColumn(name="type",discriminatorType=DiscriminatorType.STRING)  
@DiscriminatorValue(value="employee")

@Entity  
@DiscriminatorValue("regularemployee") 
```

## Hibernate Table Per Concrete

In case of Table Per Concrete class, tables are created per class.   
So there are no nullable values in the table. Disadvantage of this approach is that duplicate 
columns are created in the subclass tables.
Here, we need to use **@Inheritance(strategy = InheritanceType.TABLE_PER_CLASS)** annotation 
in the parent class and **@AttributeOverrides** annotation in the subclasses.
**@Inheritance(strategy = InheritanceType.TABLE_PER_CLASS)** specifies that we are using table per 
concrete class strategy. It should be specified in the parent class only.

```
@Entity  
@Table(name = "employee102")  
@Inheritance(strategy = InheritanceType.TABLE_PER_CLASS) 

@Entity  
@Table(name="regularemployee102")  
@AttributeOverrides({  
    @AttributeOverride(name="id", column=@Column(name="id")),  
    @AttributeOverride(name="name", column=@Column(name="name"))  
})    
```

## Hibernate Table Per Subclass

Tables are created as per persistent classes but they are treated using primary and foreign key. 
So there will not be any duplicate column in the relation.

```
@Entity  
@Table(name = "employee103")  
@Inheritance(strategy=InheritanceType.JOINED)  

@Entity  
@Table(name="contractemployee103")  
@PrimaryKeyJoinColumn(name="ID"
```

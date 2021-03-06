## Using a form
The default form to edit entities is referenced as 'Sidus\EAVModelBundle\Form\Type\DataType' and the only thing to keep
in mind is that it can't work without an entity or the "family" option.
Alternatively, you can use the 'Sidus\EAVModelBundle\Form\Type\GroupedDataType' form to separate attribute in different
fieldsets for different groups.

### DataType forms
The DataType form and those who inherit from it (GroupedDataType, TabbedDataType) allows you to automatically generate
forms to manipulate entities inside the model.

````php
<?php
/** @var \Symfony\Component\Form\FormFactoryInterface $formFactory */
$form = $formFactory->create(\Sidus\EAVModelBundle\Form\Type\DataType::class, null, [
    'family' => 'Post',
]);
````

The only required option is the ```family``` used to defines the model to use to generate the form

#### Options references

##### family
Required in most cases, used to know how to generate the fields.
Can either be the family code or the family object.

##### empty_data
Defaults to the ```FamilyInterface::createData()``` method of the family.

##### attribute
Used in embed forms to reference to the attribute holding the embed DataType. In this case, if no ```family``` option
is passed, the form will check the ```allowed_families``` option of the attribute to get the family. This will work only
if there is only a single family in the ```allowed_families``` option.

##### attributes_config
This option is a little complicated and requires a whole chapter:
[DataType form configuration](05.2-form-configuration.md)

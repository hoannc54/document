## Hiển thị columns theo quan hệ nhiều nhiều (n-n)

```
[ // Roles n-n relationship (with pivot table)
               'label'     => trans('backpack::permissionmanager.roles'),
               'type'      => 'select_multiple',
               'name'      => 'roles', // the method that defines the relationship in your Model
               'entity'    => 'roles', // the method that defines the relationship in your Model
               'attribute' => 'display_name', // foreign key attribute that is shown to user
               'model'     => config('permission.models.role'), // foreign key model
            ],
```
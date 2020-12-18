**Note: This page is under construction. Please check back later.**

# FormAPI Common Mistakes

We've seen some incorrect/unnecessary common FormAPI usages. Therefore, to help decrease these common usages, we've made a documentation for FormAPI best practices.

### Not recommended method

```php
$api = $this->getServer()->getPluginManager()->getPlugin("FormAPI"); // You can just import the SimpleForm class

// FormAPI->createSimpleForm() is deprecated
$form = $api->createSimpleForm(function (Player $player, ?int $data = null) {
    $result = $data; // Unnecessary variable assignment
    if ($result === null) return true; // This is unnecessary unless you want to do something with X button
    switch ($result) { // Empty switch case is also unnecessary
        case 0:
        break;
        case 1:
        break;
    }
});

$form->setTitle("Title");
$form->setContent("Content");
$form->addButton("Button1");
$form->addButton("Button2");
$form->sendToPlayer($player); // SimpleForm->sendToPlayer() is also deprecated

return $form; // Why do you want to return SimpleForm?
```

### Recommended method

```php
$form = new SimpleForm(function (Player $player, ?int $data = null) {});

$form->setTitle("Title");
$form->setContent("Content");
$form->addButton("Button1");
$form->addButton("Button2");

$player->sendForm($form);
```

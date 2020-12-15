**Note: This page is under construction. Please check back later.**

# FormAPI Common Mistakes

### Not recommended method

```php
$api = $this->getServer()->getPluginManager()->getPlugin("FormAPI");

$form = $api->createSimpleForm(function (Player $player, ?int $data = null) {
    $result = $data;
    if ($result === null) return true;
    switch ($result) {
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
$form->sendToPlayer($player);

return $form;
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

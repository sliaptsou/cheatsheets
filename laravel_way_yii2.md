Laravel Way in Yii2
- 
- *Факт №1*: интерфейсы в ларавеле принято называть контрактами (_Contracts_) и соответственно называть их например **WorkerContract**
- *Факт №2*: все котроллеры\модели\репозитории называть соотвествующе **IvrController\IvrModel\IvrRepository**
- *Факт №3*: поскольку мы генерим модели для ларавеля через `php artisan krlove:generate:model`, а он генерит и релейшены, то релейшены вида: 
  ```php
  return $this->belongsTo('App\Rotation'); - это заганеренные(а соответственно и не проверенные)
  return $this->belongsTo(RotationModel::class); - это уже проверенные и где-то заюзанные
  ```

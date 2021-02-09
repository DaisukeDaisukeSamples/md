# コンフィグ

以下のコードを必要な為、classより上に記述します。
```php
use pocketmine\utils\Config;
```
## Configファイルの生成
```php
//引数1:configファイルまでの場所とconfigファイル名,引数2:configファイルのフォーマット
//引数3:configファイルに入れるデータ
$this->config = new Config($this->getDataFolder() . "config.yml", Config::YAML,[
        'test' => 'data',
        'データ名(キー)' => '値'
]);
```
## configファイルに値をセット
```php
$this->config->set("データ名", "値");//値と名前を設定
```
//セーブ!!!!!!!!!!!!!!!!!! (書き込み処理に関しましては重い為、定期的な書き込みや、サーバー終了時に書き込みます事をお勧め致します...)
```php
$this->config->save();//設定を保存
```
```

```
サーバー終了時に書き込み
```php
public function onDisable(){
	$this->config->save();
}
```
## configファイルから値を取得
```php
$this->config->get("データ名");//データ名から取得
```
## configファイルに指定した名前のデータの存在を確認
```php
if($this->config->exists("データ名")){
    //ある
}else{
    //ない
}
```
## configファイルから指定のキーとデーターを削除します。
```php
$this->config->remove("削除するキー");
```
## すべてのデータを取得する
配列ですべてのデータが返ってきます。
```php
$data = $this->config->getAll();
```
//キーを取得...(通常は使用しません)
```php
$data = $this->config->getAll(true);
```
## 事前に用意したconfig.ymlファイルを使用できるようにする

plugin.ymlがあるフォルダにresourcesと言うフォルダを作っておく
そこにconfig.ymlファイルを置いておいてください
```php
※resourcesフォルダのconfig.ymlファイルに何も記載されてない場合エラーがでます。 (現在ではエラーは発生しません。)
※test:0　でもいいので データ名:値 を書いといてください
```
//$this->config変数にConfigオブジェクトを入れておく
```php
$this->saveResource("(ファイル名)", false);
$this->config = new Config($this->getDataFolder() . "config.yml", Config::YAML);
```
※config.yml以外を使用したい場合は以下のコードのようにしてください
※ファイル名にパスなどの記載は要りません。


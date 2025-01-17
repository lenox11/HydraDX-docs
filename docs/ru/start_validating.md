---
id: start_validating 
title: Старт валидации HydraDX
---

import useBaseUrl from '@docusaurus/useBaseUrl';

После [настройки узла HydraDX](/node_setup) вам необходимо связать токены HDX и установить ключи валидатора, прежде чем вы сможете начать валидацию.

:::warning

Для запуска узла валидатора требуется определенный набор технических навыков, необходимых для правильной настройки узла и обеспечения его работоспособности. Мы также требуем, чтобы валидаторы всегда запускали узел с использованием последней стабильной версии. Если вы не уверены в своих навыках в этой области, мы рекомендуем вам вместо установки собственного узла [номинировать свои HDX](/start_nominating) опытному валидатору. Тем самым вы защищаете себя и своих номинантов от непреднамеренной потери средств.

:::

## 01 Связка токенов HDX

Чтобы принять участие в сети в качестве узла валидатора, вам необходимо связать некоторое количество токенов HDX. Если у вас нет HDX, вы не сможете участвовать в _начальном_ этапе тестовой сети. Тем не менее, в ближайшие недели команда объявит некоторые интересные новости, так что оставайтесь в курсе и подпишитесь на нашу рассылку.

:::note

У вас все еще есть токены xHDX, которые вы купили во время аукциона Balancer LBP? Прежде чем продолжить, вам нужно сначала [запросить свой HDX](/claim).

:::

Чтобы связать HDX, откройте Polkadot/apps и подключитесь к одному из [общедоступных узлов HydraDX](/polkadotjs_apps_public) RPC. Убедитесь, что вы можете видеть [баланс](https://polkadot.js.org/apps/?rpc=wss%3A%2F%2Frpc-01.snakenet.hydradx.io#/accounts) своего счета.

:::warning

Связанные токены HDX застейканы для обеспечения безопасности сети. Неправильное поведение узла валидатора может быть наказано “рубкой” (слэшингом), что может привести к непреднамеренной потере средств. Мы настоятельно рекомендуем продолжать только в том случае, если вы действительно знаете, что делаете.

:::

Для следующего шага перейдите в *Network* > *Staking* > *Account actions* > *+ Stash*

<div style={{textAlign: 'center'}}>
  <img src={useBaseUrl('/validator-guide/bond-hdx-1.png')} />
</div>

После нажатия кнопки Stash вы должны увидеть настройки связывания с четырьмя редактируемыми полями:
* **stash account**: учетная запись, на которой находится большая часть ваших токенов HDX. HDX будет зачисляться с этого аккаунта.
* **controller account**: учетная запись, на которой хранится меньшая часть HDX, необходимая для покрытия сборов, связанных с запуском и остановкой процесса валидации.
* **value bonded**: количество HDX, которое вы связываете. Не связывайте все имеющиеся у вас HDX - вместо этого оставьте часть для покрытия комиссий за транзакции, которые возникнут позже.
* **payment destination**: счет, на который будут отправлены подтверждающие вознаграждения.

:::warning

Не связывайте все свои доступные токены HDX. Оставьте небольшой резерв для покрытия комиссии за транзакции. Если вы связываете все имеющиеся у вас токены HDX, вы не сможете подписать транзакцию для начала процесса валидации.

:::

После настройки параметров связывания щелкните _Bond_ и подпишите транзакцию, чтобы завершить процесс связывания.

:::caution

По соображениям безопасности не рекомендуется иметь одни и те же учетные записи Stash и Controller. Однако, поскольку переводы отключены в Snakenet, в настоящее время невозможно использовать отдельные учетные записи. Мы настоятельно рекомендуем вам переключиться на отдельные учетные записи Stash и Controller, как только это станет возможным в будущем.

:::

<div style={{textAlign: 'center'}}>
  <img src={useBaseUrl('/validator-guide/bond-hdx-2.png')} />
</div>

## 02 Генерация ключей сеанса

Второй шаг - сгенерировать ключи сеанса. Ключи сеанса используются для связывания узла валидатора с вашей учетной записью контроллера и стейкингом HDX. Поэтому важно, чтобы они были настроены правильно.

Чтобы сгенерировать ключи сеанса, запустите на узле:

```bash
$ curl -H "Content-Type: application/json" -d '{"id":1, "jsonrpc":"2.0", "method": "author_rotateKeys", "params":[]}' http://localhost:9933

# Пример вывода
{"jsonrpc":"2.0","result":"0x9257c7a88f94f858a6f477743b4180f0c9a0630a1cea85c3f47dc6ca78e503767089bebe02b18765232ecd67b35a7fb18fc3027613840f27aca5a5cc300775391cf298af0f0e0342d0d0d873b1ec703009c6816a471c64b5394267c6fc583c31884ac83d9fed55d5379bbe1579601872ccc577ad044dd449848da1f830dd3e45","id":1}
```

Вы можете найти ключи сеанса под частью результата вывода (`0x9257` … в приведенном выше примере вывода).

## 03 Установка ключа вашего сеанса

Чтобы связать сгенерированные сеансовые ключи с вашей учетной записью контроллера, откройте в Polkadot/apps:
*Developer* > *Extrinsics*

Заполните поля:

* _using selected account_: выберите свою учетную запись контроллера;
* _submit the following extrinsic_: выберите `сеанс` слева и `установите` ключи справа;
* _keys_: введите ключи сеанса из предыдущего шага;
* _proof_: `0`.

Для завершения нажмите _Submit Transaction_ и подпишите транзакцию.

<div style={{textAlign: 'center'}}>
  <img src={useBaseUrl('/validator-guide/set-session-keys-1.png')} />
</div>

## 04 Убедитесь, что ваш узел полностью синхронизирован

Прежде чем продолжить, вы должны убедиться, что ваш узел работает и процесс синхронизации полностью завершен. Самый надежный способ проверить состояние синхронизации - прямо на самом узле:

```bash

$ journalctl -f -u hydradx-validator.service

# Результат вывода будет похож на этот
Mar 22 18:37:38 Ubuntu-2010-groovy-64-minimal hydra-dx[232761]: 2021-03-22 18:37:38  💤 
Idle (52 peers), best: #622028 (0x5f5a…1041), finalized #622025 (0x5b21…a746), ⬇ 9.1kiB/s ⬆ 6.1kiB/s

```

Вы можете сравнить номер блока на выходе (в примере выше: `#622025`) с текущим номером блока, который вы можете найти в [проводнике Polkadot/apps](https://polkadot.js.org/apps/?rpc=wss%3A%2F%2Frpc-01.snakenet.hydradx.io#/explorer). На момент написания текущий блок - `#622240`, что означает, что узел, используемый для примера, не полностью синхронизирован.

Подождите, пока номер блока, показанный в ваших локальных журналах, не совпадет с текущим номером блока в сети.

## 05 Старт валидации

Чтобы начать проверку, перейдите в Polkadot / apps:

*Network* > *Staking* > *Account actions* > *Validate* (кнопка рядом с привязанным HDX)

<div style={{textAlign: 'center'}}>
  <img src={useBaseUrl('/validator-guide/validate-1.png')} />
</div>

После нажатия кнопки *Validate* вы должны увидеть всплывающее окно с названием *set validator preferences*. Здесь вам нужно установить _процент комиссии за вознаграждение_. Это доля вознаграждения, которая будет вам выплачена. Оставшиеся награды будут разделены между вашими номинантами в соответствии с их ставками. Если вы решите не брать комиссию за вознаграждение, вы можете установить процент равным 0.

Для подтверждения нажмите Validate и подпишите транзакцию.

<div style={{textAlign: 'center'}}>
  <img src={useBaseUrl('/validator-guide/validate-2.png')} />
</div>

## 06 Проверьте статус вашего узла валидатора

Вы можете проверить статус своего узла валидатора в Polkadot/apps в разделе:

*Network* > *Staking* > *Staking overview*

На этой вкладке представлен обзор всех активных валидаторов, подключенных к сети. Вверху указано количество доступных слотов валидатора, а также количество узлов, которые заявили о своем намерении стать валидатором. Вы можете подтвердить, находится ли ваш узел в очереди ожидания, щелкнув вкладку _Waiting_.

Ваш узел валидатора останется в очереди ожидания, пока он не будет выбран для включения в набор валидаторов. Набор валидаторов обновляется каждую эпоху, что позволяет включать новые узлы при условии, что есть пустые слоты.

<div style={{textAlign: 'center'}}>
  <img src={useBaseUrl('/validator-guide/validate-3.png')} />
</div>

Спасибо за поддержку HydraDX, став валидатором Snakenet! 🎉

---
id: start_nominating
title: Стать номинатором в HydraDX
---

import useBaseUrl from '@docusaurus/useBaseUrl';

Став номинатором, вы ставите часть своих токенов HDX, чтобы защитить сеть HydraDX и заработать вознаграждения. В отличие от запуска узла валидатора, процесс номинации не требует высоких технических навыков, что делает его рекомендуемым выбором для тех, кто не полностью уверен в том, что станет валидатором.

При “назначении”, номинаторы назначают свою долю валидатору по своему выбору. Таким образом, номинаторы выбирают активный набор валидаторов и получают вознаграждение за свое участие. Сумма вознаграждений, которые вы получаете в качестве номинатора, зависит от процента вознаграждения выбранного валидатора - чем выше вознаграждение валидатора, тем меньше вознаграждений вы получите за свою ставку.

:::предупреждение

Номинирование - более доступная форма участия в процессе стейкинга, однако она также несет в себе определенную степень риска. Если назначенный вами валидатор плохо себя ведет (например, не поддерживает требуемое время безотказной работы), может произойти “рубка” (слешинг), который может привести к частичной непроизвольной потере средств, которые вы поставили. Мы настоятельно рекомендуем вам проявить должную осмотрительность перед выборе валидатора.

:::

## 00 Пользовательский интерфейс стейкинга

To access the staking interface, you first need to open the Polkadot/apps, connect it to one of the [public HydraDX RPC nodes](/polkadotjs_apps_public) and make sure that you can see your account [balance](https://polkadot.js.org/apps/?rpc=wss%3A%2F%2Frpc-01.snakenet.hydradx.io#/accounts)
Чтобы получить доступ к интерфейсу стекинга, вам сначала нужно открыть Polkadot/apps, подключить его к одному из [общедоступных узлов HydraDX RPC](/polkadotjs_apps_public) и убедиться, что вы можете видеть [баланс](https://polkadot.js.org/apps/?rpc=wss%3A%2F%2Frpc-01.snakenet.hydradx.io#/accounts) своего аккаунта.

:::примечание

У вас все еще есть токены xHDX, которые вы купили во время аукциона Balancer LBP? Прежде чем продолжить, вам нужно сначала [запросить свой HDX](/claim).

:::

Убедившись, что вы видите свой баланс HDX, вы можете перейти к пользовательскому интерфейсу ставок:

*Network* > *Staking*

В пользовательском интерфейсе стекинга есть следующие вкладки меню:

* **Staking overview**: здесь вы найдете список всех активных валидаторов и некоторую базовую информацию о каждом валидаторе, такую ​​как сумма HDX, сделанная на узле, размер собственной ставки валидатора и размер комиссии за вознаграждение. Кроме того, вы можете увидеть количество очков эры, заработанных каждым валидатором в текущей эре, и номер последнего блока, созданного валидатором.
* **Account actions**: здесь вы можете делать ставки и номинировать.
* **Payouts**: здесь вы можете запросить вознаграждение за стейкинг.
* **Targets**: здесь вы можете оценить свой заработок. Это хорошее место для начала при выборе узла валидатора для номинирования.
* **Waiting**: здесь вы можете найти очередь ожидания, в которую помещаются неактивные валидаторы перед включением в активный набор валидаторов. Валидатор будет оставаться в очереди ожидания до тех пор, пока он не получит достаточное количество поставленных HDX для входа в активный набор валидаторов.
* **Validator stats**: здесь вы можете запросить тайный адрес валидатора, чтобы увидеть подробную историческую информацию о заработанных очках эпохи, выбранной ставке, наградах и слешинге. Мы настоятельно рекомендуем вам изучить эту информацию, прежде чем доверять валидатору свою номинацию.

## 01 Связка токенов HDX

:::предупреждение

Связанные токены HDX застейканы для обеспечения безопасности сети. Неправильное поведение назначенного вами узла валидатора может быть наказано рубкой (слешингом), что может привести к непреднамеренной потере ваших средств. Мы настоятельно рекомендуем вам проявить должную осмотрительность при выборе валидатора для номинации

:::

Чтобы связать токены HDX, перейдите к действиям Account actions в пользовательском интерфейсе стекинга:

*Network* > *Staking* > *Account actions* > *+ Stash*

<div style={{textAlign: 'center'}}>
  <img src={useBaseUrl('/nominator-guide/bond-hdx-1.png')} />
</div>

После нажатия кнопки *Stash* вы должны увидеть настройки связывания с четырьмя редактируемыми полями:
* **stash account**:  учетная запись, на которой находится большая часть ваших токенов HDX. HDX будет зачисляться с этого аккаунта.
* **controller account**: учетная запись, на которой хранится меньшая часть HDX, необходимая для покрытия сборов, связанных с запуском и остановкой процесса валидации.
* **value bonded**: количество HDX, которое вы связываете. Не связывайте все имеющиеся у вас HDX - вместо этого оставьте часть для покрытия комиссий за транзакции, которые возникнут позже.
* **payment destination**: счет, на который будут отправлены подтверждающие вознаграждения.

:::предупреждение

Не связывайте все свои доступные токены HDX. Оставьте небольшой резерв для покрытия комиссии за транзакции. Если вы связываете все имеющиеся у вас токены HDX, вы не сможете подписать транзакцию для начала процесса валидации.

:::

После настройки параметров связывания щелкните **Bond**  и подпишите транзакцию, чтобы завершить процесс связывания.

:::осторожно

По соображениям безопасности не рекомендуется иметь одни и те же учетные записи Stash и Controller. Однако, поскольку переводы отключены в Snakenet, в настоящее время невозможно использовать отдельные учетные записи. Мы настоятельно рекомендуем вам переключиться на отдельные учетные записи Stash и Controller, как только это станет возможным в будущем.

:::

<div style={{textAlign: 'center'}}>
  <img src={useBaseUrl('/nominator-guide/bond-hdx-2.png')} />
</div>

## 02 Номинирование валидатора

После связывания HDX вы можете назначить валидатора. Прежде чем продолжить, вы должны проявить должную осмотрительность и решить, каких валидаторов вы хотели бы назначить, исходя из их (прошлой) работы. Для этого обратитесь к информации в пользовательском интерфейсе стекинга, [описанном выше](#00-staking-ui).

Чтобы назначить одного или нескольких валидаторов, перейдите по ссылке:

*Network* > *Staking* > *Account actions* > *Nominate* (кнопка рядом с подключенным HDX)

<div style={{textAlign: 'center'}}>
  <img src={useBaseUrl('/nominator-guide/nominate-validator-1.png')} />
</div>

После нажатия кнопки *Nominate* вы должны увидеть всплывающее окно с названием *nominate validators*. Здесь вы можете выбрать одного или нескольких валидаторов из списка доступных валидаторов. Если вы выберете несколько валидаторов, вы можете распределить свою ставку в разных пропорциях между валидаторами по вашему выбору.

Чтобы назначить выбранных валидаторов, нажмите _Nominate_ и подпишите транзакцию.

<div style={{textAlign: 'center'}}>
  <img src={useBaseUrl('/nominator-guide/nominate-validator-2.png')} />
</div>


## 03 Проверьте статус своих номинирований

После завершения процесса назначения ваши номинации будут неактивны до конца текущей эпохи. Как только начнется следующая эпохи, ваши номинации станут активными при условии, что назначенные вами узлы валидатора включены в активный набор валидаторов. Если данный валидатор остается в очереди ожидания, ваша соответствующая номинация останется неактивной, и вы не получите никаких вознаграждений за эту ставку.

Чтобы проверить статус своих номинаций, перейдите по ссылке:

*Network* > *Staking* > *Account actions*

Вы можете увидеть свои неактивные номинации в разделе *Waiting nominations*:

<div style={{textAlign: 'center'}}>
  <img src={useBaseUrl('/nominator-guide/nominate-validator-3.png')} />
</div>

Как только номинация станет активной, вы должны найти ее в списке *Active nominations*

<div style={{textAlign: 'center'}}>
  <img src={useBaseUrl('/nominator-guide/nominate-validator-4.png')} />
</div>

Спасибо за поддержку HydraDX, став номинатором Snakenet! 🎉
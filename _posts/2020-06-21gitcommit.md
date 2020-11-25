---
layout: post
title:  "Настройка Ubuntu"
crawlertitle: "This is our first post"
summary: "Изучаем git"
date:   2020-06-22 23:09:47 +0700
categories: posts
tags: ['Дата аналитика']
#author: Felipe
---


# Установка Snapy

Snap-пакет — это пакет, который помимо готовой сборки самого приложения, включает в себя все необходимые зависимости и может работать (почти) в любом дистрибутиве Linux.

{% highlight python %}
sudo apt update
sudo apt install snapd
{% endhighlight %}

# Смена сочетания клавиш через утилиту Gnome Tweaks

{% highlight python %}
sudo apt install gnome-tweaks
{% endhighlight %}

Запустите утилиту Gnome Tweaks. Запустить можно из Лаунчера (иконка "Доп. настрой...").

Выберите вкладку Клавиатура и мышь и нажмите кнопку Дополнительные параметры раскладки.

Откроется окно с разворачивающимся списком настроек комбинаций клавиш. Найдите пункт Переключение на другую раскладку. 
Установите галочку напротив сочетания, которое вы хотите использовать для переключение раскладки клавиатуры.

# Установка пакетов

## Skype
{% highlight python %}
sudo snap install skype --classic
{% endhighlight %}

## Spotify
{% highlight python %}
sudo snap install spotify
{% endhighlight %}

## VLC
{% highlight python %}
sudo snap install vlc
{% endhighlight %}

## Krita
{% highlight python %}
sudo snap install krita
{% endhighlight %}

## Pycharm CE
{% highlight python %}
sudo snap install pycharm-community --classic
{% endhighlight %}

## Gimp
{% highlight python %}
udo snap install gimp
{% endhighlight %}

## Gitkraken
{% highlight python %}
sudo snap install gitkraken --classic
{% endhighlight %}

## Android-studio
{% highlight python %}
sudo snap install android-studio --classic
{% endhighlight %}

## Inkscape
{% highlight python %}
sudo snap install inkscape
{% endhighlight %}

## Sublime-text 
{% highlight python %}
sudo snap install sublime-text --classic
{% endhighlight %}

## Audacity
{% highlight python %}
sudo snap install audacity
{% endhighlight %}

## Postman
{% highlight python %}
sudo snap install postman
{% endhighlight %}

## Opera
{% highlight python %}
sudo snap install opera
{% endhighlight %}

## Telegram-desktop
{% highlight python %}
sudo snap install telegram-desktop
{% endhighlight %}

## Shotcut 
{% highlight python %}
sudo snap install shotcut --classic
{% endhighlight %}

## Chromium
{% highlight python %}
sudo snap install chromium
{% endhighlight %}

## Darktable
{% highlight python %}
sudo snap install darktable
{% endhighlight %}

## Zenkit
{% highlight python %}
sudo snap install zenkit
{% endhighlight %}

## Brave
{% highlight python %}
sudo snap install brave
{% endhighlight %}

## Electrum
{% highlight python %}
sudo snap install electrum
{% endhighlight %}

## Termius-app
{% highlight python %}
sudo snap install termius-app
{% endhighlight %}

## Miro 
{% highlight python %}
sudo snap install miro --edge
{% endhighlight %}

## Evernote
{% highlight python %}
sudo snap install evernote-web-client
{% endhighlight %}

## Slack
{% highlight python %}
sudo snap install slack --classic
{% endhighlight %}






<!---
Независимо от того, случайно ли вы зафиксировали изменения или просто поняли, что ваш предыдущий зафиксированный код - это не то, что вам нужно, часто вам потребуется отменить предыдущий коммит в Git. В этой статье рассмотрим несколько способов отменить ваши коммиты, в зависимости от вашего варианта использования.

1. Что значит вернуться или откатиться: просто посмотреть, изменить содержимое рабочей области, изменить историю Git?
2. Что именно откатить: рабочую область (worktree), индекс (область подготовки коммита, staging area), текущую ветку, удаленную ветку?
3. К какой позиции откатить: к индексу, к последнему коммиту, к произвольному коммиту?
Обозначим начальную ситуацию на следующей схеме:

Обозначим начальную ситуацию на следующей схеме:

{% highlight Ruby %}

          (i) (wt)
A - B - C - D - ? - ?
            ↑
          master
          (HEAD)
{% endhighlight %}

A, B, C, D — коммиты в ветке master.
(HEAD) — местоположение указателя HEAD.
(i) — состояние индекса Git. Если совпадает c (HEAD) - пуст. Если нет - содержит изменения, подготовленные к следующему коммиту.
(wt) — состояние рабочей области проекта (working tree). Если совпадает с (i) — нет неиндексированных изменений, если не совпадает — есть изменения.
↑ обозначает коммит, на который указывает определенная ветка или указатель.

Вот решения, в зависимости от задачи:

#### 1. Временно переключиться на другой коммит

Если вам нужно просто переключиться на другой коммит, чтобы, например, посмотреть на его содержимое, достаточно команды git checkout:

{% highlight Ruby %}
git checkout aaaaaa

 (wt)
 (i)
  A - B - C - D
  ↑           ↑
(HEAD)    master
{% endhighlight %}

Сейчас репозиторий находится в состоянии «detached HEAD». Чтобы переключиться обратно, используйте имя ветки (например, master):

{% highlight Ruby %}
git checkout master
{% endhighlight %}

#### 2. Переключиться на коммит и продолжить работу с него

Если вы хотите продолжить работу с другого коммита, вам понадобится новая ветка. Можно переключиться и создать ее одной командой:

{% highlight Ruby %}
git checkout -b имя-новой-ветки aaaaaa

 (wt)
 (i)
  A - B - C - D
  ↑           ↑
 new       master
(HEAD)
{% endhighlight %}

#### 3. Удалить изменения в рабочей области и вернуть ее к состоянию как при последнем коммите.

Начальное состояние:

{% highlight Ruby %}
       (i) (wt)
A - B - C - D - ? - ?
            ↑
          master
          (HEAD)
{% endhighlight %}

#### 3.1 Безопасно — с помощью кармана (stash)

#### 3.1.1 Только неиндексированные

Можно удалить прикарманить только те изменения, которые еще не были индексированы (командой add):

{% highlight Ruby %}
git stash save --keep-index
{% endhighlight %}

Конечное состояние:

{% highlight Ruby %}
 (wt)
               (i)       
A - B - C - D - ?         ?
            ↑             ↑
          master      stash{0}
          (HEAD)
{% endhighlight %}

#### 3.1.2 Индексированные и нет

Эта команда отменяет все индексированные и неиндексированные изменения в рабочей области, сохраняя их в карман (stash).

{% highlight Ruby %}
git stash save
{% endhighlight %}

Конечное состояние:

{% highlight Ruby %}
  (wt)
           (i)           
A - B - C - D             ?
            ↑             ↑
          master      stash{0}
          (HEAD)
{% endhighlight %}

Восстановление несохраненных изменений: легко и просто.

{% highlight Ruby %}
git stash apply
{% endhighlight %}

Если stash совсем не нужен, его можно удалить.

{% highlight Ruby %}
# удалить последнюю запись кармана
git stash drop
{% endhighlight %}

https://regexr.com/5g233

После этого восстановить изменения всё ещё можно, но сложнее: <a href='https://stackoverflow.com/q/89332/2790048'>How to recover a dropped stash in Git?</a> ?

#### 3.2 Опасный способ

<b>Осторожно!</b> Эта команда безвозвратно удаляет несохраненные текущие изменения из рабочей области и из индекса Если они вам все-таки нужны, воспользуйтесь git stash.

Восстановление несохраненных изменений: неиндексированные потеряны полностью, но <a href='https://ru.stackoverflow.com/a/424384/181472'>вы можете восстановить то, что было проиндексировано</a>.

Здесь мы будем использовать git reset --hard

Выполняем:

{% highlight Ruby %}
git reset --hard HEAD
{% endhighlight %}

Конечное состояние:

{% highlight Ruby %}
      (wt)
           (i)
A - B - C - D - х - х
            ↑
          master
          (HEAD)
{% endhighlight %}

#### 4. Перейти к более раннему коммиту в текущей ветке и удалить из нее все последующие (неопубликованные)

<b>Осторожно!</b>Эта команда переписывает историю Git-репозитория. Если вы уже опубликовали <a href='https://ru.stackoverflow.com/tags/git-push/info'>(git push) </a>свои изменения, то этот способ использовать нельзя <a href='https://ru.stackoverflow.com/questions/429512/'>(см. почему)</a>. Используйте вариант из пункта 5 <a href='https://ru.stackoverflow.com/tags/git-revert/info'>(git revert)</a>.

#### 4.1 При этом сохранить изменения в индекс репозитория:

{% highlight Ruby %}
git reset --soft bbbbbb
{% endhighlight %}

После этого индекс репозитория будет содержать все изменения от cccccc до dddddd. Теперь вы можете сделать новый коммит (или несколько) на основе этих изменений.

{% highlight Ruby %}
           (wt)
           (i)
A - B - C - D 
    ↑
  master
  (HEAD)
{% endhighlight %}

#### 4.2 Сохранить изменения в рабочей области, но не в индексе.

{% highlight Ruby %}
git reset bbbbbb
{% endhighlight %}

Эта команда просто перемещает указатель ветки, но не отражает изменения в индексе (он будет пустым).

{% highlight Ruby %}
 (i)     (wt)
A - B - C - D 
    ↑
  master
  (HEAD)
{% endhighlight %}

#### 4.3 Просто выбросить изменения.

<b>Осторожно!</b> Эта команда безвозвратно удаляет несохраненные текущие изменения. Если удаляемые коммиты не принадлежат никакой другой ветке, то они тоже будут потеряны.

<b>Восстановление коммитов:</b> Используйте <a href='https://ru.stackoverflow.com/tags/git-reflog/info'>git reflog</a> и <a href='https://ru.stackoverflow.com/questions/232455/'>этот вопрос</a>этот вопрос чтобы найти и восстановить коммиты; иначе сборщик мусора удалит их безвозвратно через некоторое время.

Восстановление несохраненных изменений: неиндексированные потеряны полностью, но <a href='https://ru.stackoverflow.com/a/424384/181472'>вы можете восстановить то, что было проиндексировано</a>вы можете восстановить то, что было проиндексировано.

Начальное состояние:

{% highlight Ruby %}
   (i) (wt)
A - B - C - D - ? -  ?
            ↑
          master
          (HEAD)
{% endhighlight %}

Выполняем:

{% highlight Ruby %}
git reset --hard bbbbbb
{% endhighlight %}

Конечное состояние:

{% highlight Ruby %}
 (wt)
   (i)
A - B - C - D - х - х
    ↑
  master
  (HEAD)
{% endhighlight %}

#### 

5. Отменить уже опубликованные коммиты с помощью новых коммитов
Воспользуйтесь командой <a href='https://ru.stackoverflow.com/tags/git-revert/info'>git revert</a>. Она создает новые коммиты, по одному на каждый отменяемый коммит. Таким образом, если нужно отменить все коммиты после aaaaaa:

{% highlight Ruby %}
 # можно перечислить отменяемые коммиты
git revert bbbbbb cccccc dddddd

# можно задать диапазон от более раннего к более позднему (новому)
git revert bbbbbb..dddddd

# либо в относительных ссылках
git revert HEAD~2..HEAD

# можно отменить коммит слияния, указывая явным образом номер предка (в нашем примере таких нет):
git revert -m 1 abcdef

# после этого подтвердите изменения:
git commit -m'детальное описание, что и почему сделано'
{% endhighlight %}

<b>Восстановление:</b> Если revert-коммит оказался ошибочным, <a href='https://ru.stackoverflow.com/a/433111/181472'>используйте этот ответ</a>.

--->
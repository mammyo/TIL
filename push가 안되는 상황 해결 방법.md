# push가 안되는 상황 해결 방법

* 원격 저장소 이력과 로컬 저장소 이력이 다른경우 아래와 같이 push가 되지 않는다.

```bash
$git push origin master
To https://github.com/mammyo/git_tutorial.git
 ! [rejected]        master -> master (fetch first)
 # 원격 저장소 이력과 로컬 저장소 이력이 다름
error: failed to push some refs to 'https://github.com/mammyo/git_tutorial.git'
hint: Updates were rejected because the remote contains work that you do
hint: not have locally. This is usually caused by another repository pushing
hint: to the same ref.
 # 원격 저장소 변경 사항들을 먼저 통함(integrate)하고 싶을텐데..??
 # 다시 push 하기전에 pull을 해봐
You may want to first integrate the remote changes
hint: (e.g., 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details


```

* 아래와 같이 해결한다.

  ```bash
  $git pull origin master
  
  ```

  * pull을 하기되면, commit 메시지를 작성할 수 있는 vim이 뜨게 된다.\

  * `esc`,`:wq`를 순서대로 입력하면 커밋 메시지를 저장 할 수있다.

    ```bash
    $ git log --oneline -1
    138afb0 (HEAD -> master) Merge branch 'master' of https://github.com/mammyo/git_tutorial
    ```

  * 그리고 다시 `push`한다.

    ```bash
    $git push origin master
    ```

* `pull`을 하는 과정에서 각각 이력이 동일한 파일을 수정했다면, 충돌이 발생한다!

* 충돌이 발생하는 경우 직접 해당 파일을 열어서 수정하고, commit을 한다.

  ```bash
  $git add .
  $git comit
  ```

* commit 메시지는 자동으로 입력이 되어있고, 종료한 이후에는 다시 `push` 한다.


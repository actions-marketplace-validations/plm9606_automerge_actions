[ENG πΊπΈ](#Automatically-Merge-PR-Actions) / [νκ΅­μ΄ π°π·](#μλ-λ¨Έμ§-Actions)

# Automatically Merge PR Actions

A GitHub Action to automatically merge Pull Requests.

If you add a specific label, the action will then check the number of reviews.

If the number of reviews is more than one, the PR is automatically merged.

If you add other lables, the action will be passed.

<!-- Screenshot -->

# Usage

Create a `.github/workflows/${YOUR_WORKFLOW_NAME}.yml` file in your GitHub repo and add the following code.

```yml
name: Check PR can be merged
on:
  pull_request:
    types: [labeled]
    branches:
      - develop/* # The branch you want to automatically merge pull request
jobs:
  Run Actions:
    runs-on: ubuntu-latest
    steps:
      - name: Automatically Merge PR
        uses: plm9606/automerge_actions@1.2.2
        with:
          # The label name to automatically merge. Default is "automerge".
          label-name:
          # The number of reviewers to automatically merge. Default is 1.
          reviewers-number:
          # The merge method ("merge", "squash", "rebase"). Default is "merge"
          merge-method:
          # Let the bot delete the merged branch. true or false.
          auto-delete:
          # GitHub WebHook Secret Token
          github-token: ${{ secrets.GITHUB_TOKEN }}
```

## Inputs

### 1. label-name

Not required, default is `automerge`.

The label name the action uses to merge, before checking for reviews.

### 2. reviewers-number

Not required, default is `1`.

The number of reviewers the action uses to merge, after checking the label.

### 3. merge-method

Not required, default is `merge`.

The merge method: merge, squash or rebase.

### 4. auto-delete

Not required, default is `false`.

If you define `true`, the bot will delete the merged branch.

### 5. github-token

Required.
You have to get `Personal access token` from GitHub. And create GitHub secrets in your repo.([How to?](https://help.github.com/en/actions/automating-your-workflow-with-github-actions/creating-and-using-encrypted-secrets))

The secret name may be different from the example above.

## Log Messages

`Success Merge PR!`: Success merge automatically.

`You don't labeled auto merge label::"${labelName}"`: If you intend to merge automatically, check the merge label name.

`You need to get other's review!` : Error. You must receive PR review(s).

# μλ λ¨Έμ§ Actions

PRμ νΉμ  λΌλ²¨μ λ¬κ² λλ©΄ ν΄λΉ PRμ λ¬λ¦° λ¦¬λ·°μ μλ₯Ό νμΈν©λλ€.

μ€μ ν μ μ΄μμ λ¦¬λ·°κ° λ¬λ¦΄ κ²½μ° μλμΌλ‘ νλ¦¬νμ€νΈκ° λ¨Έμ§λ©λλ€.

actionμμ μ€μ νμ§ μμ λΌλ²¨μ λ¬κ²λλ©΄ μ€ν΅λ©λλ€.

<!-- Screenshot -->

# μ¬μ©λ²

`.github/workflows/${YOUR_WORKFLOW_NAME}.yml` μ μλμ κ°μ΄ μ‘μ μ€μ  μ€ν¬λ¦½νΈλ₯Ό μμ±ν©λλ€.

```yml
name: Check PR can be merged
on:
  pull_request:
    types: [labeled]
    branches:
      - develop/* # ν΄λΉ κΈ°λ₯μ μ¬μ©νκ³  μΆμ λΈλμΉλ₯Ό μ μν©λλ€
jobs:
  Run Actions:
    runs-on: ubuntu-latest
    steps:
      - name: Automatically Merge PR
        uses: plm9606/automerge_actions@1.2.2
        with:
          # μ΄λ²€νΈλ₯Ό νΈλ¦¬κ±°νκ³  μΆμ λΌλ²¨ μ΄λ¦μ μ€μ ν©λλ€. κΈ°λ³Έ μ΄λ¦μ "automerge" μλλ€.
          label-name:
          # μ΅μ λ¦¬λ·°μ΄ μλ₯Ό μ§μ ν  μ μμ΅λλ€. κΈ°λ³Έμ 1λͺμλλ€.
          reviewers-number:
          # "merge", "squash", "rebase" μ€ νκ°μ§λ₯Ό μ νν  μ μμ΅λλ€. κΈ°λ³Έκ°μ "merge" μλλ€
          merge-method:
          # GitHub WebHook Secret Token
          github-token: ${{ secrets.GITHUB_TOKEN }}
```

## Inputs

### 1. label-name

Not required, default is `automerge`.

μλ λ¨Έμ§ μ΄λ²€νΈλ₯Ό νΈλ¦¬κ±°νκΈ° μν λΌλ²¨ μ΄λ¦μλλ€.

### 2. reviewers-number

Not required, default is `1`.

λ¦¬λ·°μ΄μ μλ₯Ό μ§μ ν©λλ€.

### 3. merge-method

Not required, default is `merge`.

μ ν κ°λ₯ν λ©μλ: merge, squash, rebase.

### 4. auto-delete

Not required, default is `false`.

`true`λ‘ μ€μ  μ λ¨Έμ§ μμ μ΄ν λ΄μ΄ μλμΌλ‘ λ¨Έμ§λ λΈλμΉλ₯Ό μ­μ ν©λλ€.

### 4. github-token

**Required.**

κΉνλΈμ `Personal access token` κ° νμν©λλ€. κ·Έλ¦¬κ³  ν΄λΉ ν ν°μ μ¬μ©νκ³ μ νλ λ ν¬μ secretsλ‘ λ±λ‘ν΄μ£Όμ΄μΌ ν©λλ€.([How to?](https://help.github.com/en/actions/automating-your-workflow-with-github-actions/creating-and-using-encrypted-secrets))

## Log Messages

`Success Merge PR!`: μ±κ³΅μ μΌλ‘ λ¨Έμ§κ° λμμ΅λλ€

`You don't labeled auto merge label::"${labelName}"`: λ¨Έμ§ λΌλ²¨λ‘ μ€μ ν λΌλ²¨μ΄ λ¬λ €μμ§ μμ κ²½μ° λνλ©λλ€. ν΄λΉ μ‘μμ μ¬μ©νκ³ μ ν κ²μ΄μλ€λ©΄ λΌλ²¨μ λ¬μμ£Όμ΄μΌ ν©λλ€.

`You need to get other's review!` : λ¦¬λ·°μκ° λΆμ‘±ν©λλ€.

# Lab: Unprotected admin functionality

## 概要
このLabでは管理者権限がきちんと保護されていない脆弱性を扱う。  
目的は脆弱性を理解し、それに対する攻撃手法を学ぶことである。

---

## 脆弱性の種類
Access Control

---

## 攻撃の結論（最短）
- URLにrobots.txtをいれて調べたら、adminページのディレクトリの場所があった。
---

## 攻撃の流れ

### 1. 観察
- （画面を見てわかったこと）

---

### 2. 仮説
- （どんな脆弱性だと考えたか）
- Vertical privilege escalationの基本のUnprotected functionalityだと予想

---

### 3. 検証
- URLに直打ちでrobots.txtと打って検索
- 結果：
  - admのWebページのディレクトリの場所が書いてあった。

---

### 4. 成功条件・根拠
- 対象アカウントの削除

---

## 使用ツール
- Burp Suite（`Proxy``）

---

## 学んだこと
- （このLabで理解できたこと）
- この問題の解く時の思考手順
- 1.admin URLを探す
-   /admin、/admin-panel、/administrator、/manage、/dashboard
- 2.robots.txtを探す
- （次回以降に活かせるポイント）
- （注意すべき挙動や見分け方）

---

## メモ（任意）
ここの脆弱性について
管理者機能へのアクセスに認可チェックがなく、admin URLへ直接アクセスすることで一般ユーザーでもユーザー削除が可能だった。
隠すことによるセキュリティ（Security through obscurity)は通用しない（サーバーでアクセス制御すべき）
バックエンドの各エンドポイントでの「認可（Authorization）」の必須性
(本来なら、アクセスされた時点でセッション情報を確認して今アクセスしたユーザーは管理者権限を持っているかを
厳格なif文で処理し403 Forbiddenやトップページへのリダイレクトするべき）

# コーディング規約

### 目次

1. [目的](#目的)
2. [基本方針](#基本方針)
3. [命名規則](#命名規則)
4. [ディレクトリ構成](#ディレクトリ構成)
5. [CSS](#CSS)

---

### 目的

本規約は、チームで開発するソフトウェアの**可読性・保守性・品質・一貫性**を向上させ、開発効率を高めることを目的とする。

個人の好みではなく、チームとして共通のルールを定めることで、以下を実現する。

- コードを誰が読んでも理解しやすくする
- コードレビューの負担を軽減する
- バグや不具合の発生を抑える

---

### 基本方針

#### 可読性

コードは「書く人」ではなく「後から読む人」が理解しやすいことを優先する。

- 適切な変数名・関数名を付ける
- 1つの処理に責務を詰め込みすぎない
- 複雑な処理は適切に分割する
- 必要以上に短いコードを書くことを目的としない

#### 一貫性

既存のコードやプロジェクト内のルールを優先する。

同じ目的の処理について、場所によって異なる書き方をしない。

#### DRY原則

同じ処理やロジックを複数箇所にコピーしない。

ただし、無理に共通化してコードが複雑になる場合は、可読性を優先する。

#### KISS原則

必要以上に複雑な実装を避け、できるだけ単純な実装を選択する。

#### YAGNI

現時点で必要のない機能や拡張性を、先回りして実装しない。

---

### 命名規則
| 対象 | 規則 | 例 |
| --- | --- | --- |
| コンポーネント | PascalCase | `UserProfile` |
| コンポーネントファイル | PascalCase | `UserProfile.tsx` |
| 変数 | lowerCamelCase | `userName` |
| 関数 | lowerCamelCase | `fetchUsers` |
| イベントProps | `on` \+ PascalCase | `onSubmit` |
| イベントハンドラ | `handle` \+ PascalCase | `handleSubmit` |
| Boolean | `is` / `has` / `can` / `should` | `isLoading` |
| State | `[xxx, setXxx]` | `[user, setUser]` |
| カスタムHook | `use` \+ PascalCase | `useAuth` |
| Props型 | PascalCase + `Props` | `UserCardProps` |
| 型 | PascalCase | `User` |
| Context | PascalCase + `Context` | `AuthContext` |
| Provider | PascalCase + `Provider` | `AuthProvider` |
| 定数 | UPPER\_SNAKE\_CASE | `MAX_RETRY_COUNT` |
| 配列 | 原則複数形 | `users` |

---

### コンポーネント

#### 4.1 コンポーネント名

Reactコンポーネントは **PascalCase** で命名する。

##### OK

```tsx
function UserProfile() {
  return <div />;
}

function SearchForm() {
  return <form />;
}
```

##### NG

```tsx
function userProfile() {
  return <div />;
}

function user_profile() {
  return <div />;
}
```

---

#### 4.2 コンポーネント名は役割を表す

可能な限り、コンポーネントの責務が名前から分かるようにする。

##### 推奨

```
UserProfile
UserList
UserCard
SearchForm
LoginForm
NavigationMenu
ErrorMessage
LoadingSpinner
```

##### 非推奨

```
Common
Component
Content
Box
Container
Data
Item
```

ただし、プロジェクト内で明確な役割を持つ共通コンポーネントについては使用してよい。

---

### ファイル名

#### 5.1 Reactコンポーネント

コンポーネントファイルは、コンポーネント名と一致させる。

```
UserCard.tsx
UserProfile.tsx
SearchForm.tsx
```

```tsx
// UserCard.tsx
export function UserCard() {
  return <div />;
}
```

---

#### 5.2 Hook

カスタムHookは `use` から始め、ファイル名もHook名と一致させる。

```
useAuth.ts
useUser.ts
useFetchUsers.ts
```

---

#### 5.3 テスト

テスト対象のファイル名に `.test` を付ける。

```
UserCard.test.tsx
useUser.test.ts
```

---

### 6. 変数

変数は **lowerCamelCase** で命名する。

```ts
const userName = "Taro";
const userList = [];
const selectedUser = null;
const currentPage = 1;
```

---

#### 意味のない変数名を避ける

##### OK

```tsx
const user = getUser();
const userName = getUserName();
const totalPrice = calculateTotal();
```

```tsx
const formData = {};
const inputValue = "";
const responseData = response.data;
```

##### NG

```tsx
const data = getUser();
const value = getUserName();
const obj = getUser();
const tmp = calculateTotal();
```

ただし、名前そのものが意味を持つ場合や限定されたスコープ内では使用してよい。

---

### 関数

関数は **lowerCamelCase** で命名する。

原則として、関数名には処理内容を表す動詞を含める。

```tsx
getUser();
fetchUsers();
createUser();
updateUser();
deleteUser();

validateForm();
calculateTotal();
formatDate();
```

---

#### CRUD系

 以下を基本とする。

| 処理 | 命名 |
| --- | --- |
| 取得 | `get` / `fetch` |
| 作成 | `create` |
| 更新 | `update` |
| 削除 | `delete` |
| 検証 | `validate` |
| 計算 | `calculate` |
| 変換 | `convert` |
| 整形 | `format` |

```tsx
fetchUsers();
createUser();
updateUser();
deleteUser();
validateUser();
formatUserName();
```

---

### イベント

#### 8.1 イベントProps

コンポーネントがPropsとして受け取るイベント関数には、`on` を使用する。

```tsx
type UserFormProps = {
  onSubmit: () => void;
  onCancel: () => void;
};

type UserCardProps = {
  onClick: () => void;
};
```

---

#### 8.2 イベントハンドラ

コンポーネント内部でイベントを処理する関数には、`handle` を使用する。

```tsx
const handleClick = () => {};

const handleSubmit = () => {};

const handleChange = () => {};

const handleDelete = () => {};
```

---

### Boolean

Boolean型の変数・Props・Stateは、原則として以下の接頭辞を使用する。

- `is`：状態
- `has`：所有・存在

```tsx
const isLoading = true;
const isOpen = false;
const isActive = true;

const hasError = false;
const hasPermission = true;
```

##### NG

```tsx
const loading = true;
const open = false;
const error = false;
```

---

### State

`useState` のStateと更新関数は以下の形式にする。

```
[状態, set + 状態]
```

```tsx
const [user, setUser] = useState<User | null>(null);

const [count, setCount] = useState(0);

const [isOpen, setIsOpen] = useState(false);

const [isLoading, setIsLoading] = useState(false);
```

---

#### 10.1 Boolean State

Boolean Stateには `is` / `has` を使用する。

```tsx
const [isOpen, setIsOpen] = useState(false);

const [isLoading, setIsLoading] = useState(false);

const [hasError, setHasError] = useState(false);
```

---

### Props

#### 11.1 Props名

Propsは **lowerCamelCase** で命名する。

```tsx
type UserCardProps = {
  user: User;
  isActive: boolean;
  isDisabled: boolean;
  onClick: () => void;
};
```

---

#### 11.2 イベントProps

イベントは `on` を使用する。

```
onClick
onSubmit
onChange
onCancel
onDelete
```

---

#### 11.3 Props型

コンポーネント固有のProps型

```
コンポーネント名 + Props
```

```tsx
type UserCardProps = {};

type UserFormProps = {};

type SearchFormProps = {};
```

---

### Type / Interface

型およびinterfaceは **PascalCase** とする。

```tsx
type User = {
  id: string;
  name: string;
};

interface Product {
  id: string;
  name: string;
}
```

---

#### 12.1 `Type` / `Interface` を名前に含めない

原則として以下は禁止する。

```tsx
type UserType = {};

interface UserInterface {}
```

以下を推奨する。

```tsx
type User = {};

interface User {}
```

---

### 型とPropsの使い分け

ドメインモデルを表す型

```tsx
type User = {
  id: string;
  name: string;
};
```

コンポーネントのProps

```tsx
type UserCardProps = {
  user: User;
  isActive: boolean;
};
```

このように、**データそのものとコンポーネントの入力値を区別する**。

---

### カスタムHook

カスタムHookは **`use` \+ PascalCase** とする。

```
useAuth();
useUser();
useUsers();
useFetchUsers();
useLocalStorage();
```

---

#### 14.1 Hookの命名

Hook名から取得・操作対象が分かるようにする。

```
useUser();
useCart();
useAuth();
useSearch();
usePagination();
```

##### NG

```
useData();
useCommon();
useHelper();
useUtil();
```

---

### Context

Contextは **`名前 + Context`** とする。

```tsx
const AuthContext = createContext<AuthContextValue | null>(null);

const UserContext = createContext<UserContextValue | null>(null);

const ThemeContext = createContext<ThemeContextValue | null>(null);
```

Providerは **`名前 + Provider`** とする。

```tsx
function AuthProvider() {
  return <AuthContext.Provider>{/* ... */}</AuthContext.Provider>;
}
```

使用例

```tsx
<AuthProvider>
  <App />
</AuthProvider>
```

---

### 定数

アプリケーション全体で変更されない定数は、原則として **UPPER\_SNAKE\_CASE** を使用する。

```tsx
const MAX_RETRY_COUNT = 3;

const DEFAULT_PAGE_SIZE = 20;

const API_TIMEOUT_MS = 5000;
```

---

#### 16.1 コンポーネント内の値

コンポーネント内部でのみ使用し、通常のローカル変数として扱う値はlowerCamelCaseとしてよい。

```tsx
function UserList() {
  const pageSize = 20;

  return <div />;
}
```

---

### 配列

配列は原則として複数形で命名する。

```tsx
const users = [];
const products = [];
const messages = [];
const orders = [];
```

単一の要素は単数形とする。

```tsx
const user = {};
const product = {};
const message = {};
const order = {};
```

---

### Map / Filter / Reduce

コレクション操作では、要素の意味が分かる変数名を使用する。

#### 推奨

```tsx
users.map((user) => (
  <UserCard key={user.id} user={user} />
));
```

#### 非推奨

```tsx
users.map((item) => (
  <UserCard key={item.id} user={item} />
));
```

ただし、対象の意味が明確な場合は `item` などの汎用名を使用してよい。

---

### API関連

APIクライアントやデータ取得関数は、責務が分かる命名にする。

```
fetchUsers();
fetchUserById();
createUser();
updateUser();
deleteUser();
```

---

### 非同期処理

Promiseを返す関数については、処理内容が分かる動詞を使用する。

```
fetchUsers();
loadUser();
saveUser();
submitForm();
```

#### 推奨

```tsx
async function fetchUsers() {}
```

#### 非推奨

```tsx
async function fetchUsersAsync() {}
```

---

### エラー関連

エラーを表す変数には、可能な限り意味を明確にする。

```tsx
const error = null;

const userError = null;

const validationError = null;

const apiError = null;
```

Booleanの場合は以下を使用する。

```tsx
const hasError = false;

const hasValidationError = false;

const hasApiError = false;
```

---

### 日付・時間

日付や時間を表す変数には、単位や意味が分かる名前を付ける。

```tsx
const createdAt = new Date();

const updatedAt = new Date();

const startDate = new Date();

const endDate = new Date();

const timeoutMs = 5000;
```

単位が重要な数値には単位を名前に含める。

```tsx
const TIMEOUT_MS = 5000;
const RETRY_INTERVAL_MS = 1000;
const MAX_AGE_DAYS = 30;
```

---

### ID

IDを表す変数は原則として `id` を使用する。

```tsx
const userId = user.id;
const productId = product.id;
const orderId = order.id;
```

複数のIDが存在する場合は対象を明示する。

```tsx
const userId = "user-001";
const organizationId = "org-001";
const projectId = "project-001";
```

---

### CSS / className

`className` は、コンポーネントや要素の役割が分かる名前にする。

```tsx
<div className="user-card">
  <div className="user-card__header">
    ...
  </div>
</div>
```

CSS Modulesを使用する場合は、プロジェクトのCSS命名規則に従う。

```tsx
import styles from "./UserCard.module.css";

<div className={styles.userCard} />
```

JavaScript / TypeScriptの変数名とCSSのクラス名を混同しない。

```
TypeScript → camelCase
CSS        → プロジェクトで定めたCSS規則
```

---

### コンポーネントのディレクトリ構成

コンポーネント単位で関連ファイルをまとめる場合は、以下を基本形とする。

```
components/
└── UserCard/
    ├── UserCard.ts
    ├── UserCard.tsx
    ├── UserCard.test.tsx
    ├── UserCard.module.css
    └── index.ts
```

Hookは以下を基本とする。

```
hooks/
├── useAuth.ts
├── useUser.ts
└── useFetchUsers.ts
```

型は以下を基本とする。

```
types/
├── user.ts
├── product.ts
└── order.ts
```

---

### `index.ts` の利用

外部から利用するコンポーネントについては、`index.ts` からexportする。

```tsx
export { UserCard } from "./UserCard";
```

利用側

```tsx
import { UserCard } from "@/components/UserCard";
```

---

### Boolean Propsの例

```tsx
type ModalProps = {
  isOpen: boolean;
  isClosable: boolean;
  onClose: () => void;
};
```

使用例

```tsx
<Modal
  isOpen={isOpen}
  isClosable={true}
  onClose={handleClose}
/>
```

---

### コンポーネントの命名例

親子関係や責務が名前から分かるようにする。

```
UserList
  └── UserCard

UserForm
  ├── UserFormField
  └── UserFormActions

ProductList
  └── ProductCard

SearchPage
  ├── SearchForm
  ├── SearchResultList
  └── SearchResultCard
```

---

### 避けるべき命名

以下のような名前は、原則として使用しない。

```
Common
CommonComponent
Component
Data
DataComponent
Util
Utils
Helper
Manager
Thing
Stuff
Temp
Tmp
Test
Foo
Bar
```

ただし、プロジェクト上で明確な責務を持ち、名前として意味が成立している場合は除く。

---

### 略語

原則として、意味が分かりにくい略語は使用しない。

#### NG

```tsx
const usr = {};
const usrInfo = {};
const btn = {};
const msg = {};
const cnt = 0;
```

#### OK

```tsx
const user = {};
const userInfo = {};
const button = {};
const message = {};
const count = 0;
```

ただし、一般的な略語は使用してよい。

```tsx
const id = user.id;
const url = user.url;
const api = createApi();
const httpClient = createHttpClient();
```

---

### 命名の長さ

短い名前にすることを目的とせず、意味が伝わることを優先する。

#### 非推奨

```tsx
const d = new Date();
const u = getUser();
```

#### 推奨

```tsx
const currentDate = new Date();
const user = getUser();
```

一方で、過度に長い名前も避ける。

```tsx
// 非推奨
const currentAuthenticatedUserInformation = getUser();

// 推奨
const currentUser = getUser();
```

---

### 変数の再利用

異なる意味を持つ値に同じ変数を再利用しない。

#### NG

```tsx
let data = getUser();

data = getProducts();
```

#### OK

```tsx
const user = getUser();
const products = getProducts();
```

変数名は、その変数が保持している値の意味を一貫して表すものとする。

---

### コンポーネント例

以下を標準的な実装例とする。

```tsx
type UserCardProps = {
  user: User;
  isActive: boolean;
  onClick: (userId: string) => void;
};

export function UserCard({
  user,
  isActive,
  onClick,
}: UserCardProps) {
  const handleClick = () => {
    onClick(user.id);
  };

  return (
    <button
      type="button"
      className={isActive ? "active" : ""}
      onClick={handleClick}
    >
      {user.name}
    </button>
  );
}
```

この例では、

```
UserCard      → コンポーネント：PascalCase
UserCardProps → Props型：PascalCase + Props
user          → データ：camelCase
isActive      → Boolean：is + 名前
onClick       → イベントProps：on + 名前
handleClick   → イベントハンドラ：handle + 名前
```

という規則を適用している。

---

### カスタムHook例

```tsx
type UseUserResult = {
  user: User | null;
  isLoading: boolean;
  hasError: boolean;
};

export function useUser(userId: string): UseUserResult {
  const [user, setUser] = useState<User | null>(null);
  const [isLoading, setIsLoading] = useState(false);
  const [hasError, setHasError] = useState(false);

  // ...

  return {
    user,
    isLoading,
    hasError,
  };
}
```

---

### 命名に迷った場合

命名に迷った場合は、以下の順序で判断する。

1. ドメイン上の正式名称がある場合は、それを使用する
2. 既存コードで同じ概念に使用されている名称を確認する
3. React / TypeScriptの一般的な慣習に従う
4. 略語を避ける
5. 名前から役割が分かるか確認する
6. チーム内で判断できない場合はコードレビューで合意する

---

### 命名チェックリスト

Pull Requestでは、以下を確認する。

- [ ] コンポーネントがPascalCaseになっている
- [ ] 変数・関数がcamelCaseになっている
- [ ] Booleanに`is` / `has` が適切に付いている
- [ ] イベントPropsが`onXxx`になっている
- [ ] イベントハンドラが`handleXxx`になっている
- [ ] カスタムHookが`useXxx`になっている
- [ ] Props型が`XxxProps`になっている
- [ ] 型名がPascalCaseになっている
- [ ] 定数が適切に命名されている
- [ ] 配列が原則として複数形になっている
- [ ] 不要な略語を使用していない
- [ ] `data`、`value`、`temp`など意味の曖昧な名前を乱用していない
- [ ] 名前から変数・関数・コンポーネントの役割が判断できる

---

### 最低限守るべきルール

すべてのルールを覚える必要はない。最低限、以下を必須ルールとする。

```
コンポーネント  → PascalCase
変数             → camelCase
関数             → camelCase
Boolean          → is / has
イベントProps    → onXxx
イベント処理     → handleXxx
State            → [xxx, setXxx]
カスタムHook     → useXxx
Props型          → XxxProps
型               → PascalCase
定数             → UPPER_SNAKE_CASE
配列             → 原則複数形
```

---

### 画面基準サイズ

画面実装は **1440px幅を基準** とします。

実装時はブラウザのデベロッパーツールを使用し、**1440px幅の表示を基準としてレイアウトを確認**してください。

また、必要に応じて1440px以外の画面幅でも確認し、レイアウト崩れがないことを確認してください。
※ レスポンシブ対応をする必要はございません

#### 注意事項

- 1440pxを固定値として width: 1440px のように指定しないでください。
- コンテンツ幅やレイアウトは、必要に応じて max-width、width: 100%、min()、max() などを使用して柔軟に設計してください。

---

### ディレクトリ構成

コンポーネントは component ディレクトリ配下 に実装してください。

基本的な構成は以下の形式とします。

```
component/
└── ComponentName/
    ├── index.tsx
    └── styles.module.css
```

例：
```
component/
└── Sample/
    ├── index.tsx
    └── styles.module.css
```

既に Sample コンポーネントを作成しているため、新規コンポーネントを実装する際は、Sampleコンポーネントのディレクトリ構造・ファイル構成を参考にしてください。

---

### CSS

CSSは **CSS Modules** を使用してください。

コンポーネントごとにCSS Modulesを適用し、グローバルなCSSへの依存をできるだけ避けてください。

#### CSSファイル名

CSSファイルは必ず以下のファイル名で統一してください。

```
styles.module.css
```

例：
```
Sample/
├── index.tsx
└── styles.module.css
```

index.tsx では以下のようにCSS Modulesを読み込んで使用します。

```
import styles from './styles.module.css';

export const Sample = () => {
  return (
    <div className={styles.container}>
      ...
    </div>
  );
};
```

#### 注意事項

- コンポーネント固有のスタイルをグローバルCSSに記述しないでください。
- クラス名はCSS Modulesを前提として、コンポーネント内で意味が分かる名前を付けてください。

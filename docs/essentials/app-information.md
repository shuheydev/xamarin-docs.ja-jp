---
title: 'Xamarin.Essentials: アプリ情報'
description: このドキュメントでは、アプリケーションに関する情報を提供する Xamarin.Essentials の AppInfo クラスについて説明します。 たとえば、アプリの名前やバージョンが公開されます。
ms.assetid: 15924FCB-19E0-45B2-944E-E94FD7AE12FA
author: jamesmontemagno
ms.author: jamont
ms.date: 11/04/2018
ms.openlocfilehash: 3e67b605e485b724ec11f2ac94dcf3d1aa77d5cf
ms.sourcegitcommit: be6f6a8f77679bb9675077ed25b5d2c753580b74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/07/2018
ms.locfileid: "53057300"
---
# <a name="xamarinessentials-app-information"></a>Xamarin.Essentials: アプリ情報

**AppInfo** クラスでは、アプリケーションに関する情報が提供されます。

## <a name="get-started"></a>作業開始

[!include[](~/essentials/includes/get-started.md)]

## <a name="using-appinfo"></a>AppInfo の使用

自分のクラスの Xamarin.Essentials に参照を追加します。

```csharp
using Xamarin.Essentials;
```

## <a name="obtaining-application-information"></a>アプリケーションの情報の取得:

API では次の情報が公開されます。

```csharp
// Application Name
var appName = AppInfo.Name;

// Package Name/Application Identifier (com.microsoft.testapp)
var packageName = AppInfo.PackageName;

// Application Version (1.0.0)
var version = AppInfo.VersionString;

// Application Build Number (1)
var build = AppInfo.BuildString;
```

## <a name="displaying-application-settings"></a>アプリケーションの設定の表示

**AppInfo** クラスでは、アプリケーションに関してオペレーティング システムで保持されている設定のページも表示できます。

```csharp
// Display settings page
AppInfo.ShowSettingsUI();
```

この設定ページでは、アプリケーションのアクセス許可を変更したり、プラットフォーム固有の他のタスクを実行したりできます。

## <a name="platform-implementation-specifics"></a>プラットフォームの実装の詳細

# <a name="androidtabandroid"></a>[Android](#tab/android)

アプリの情報は、`AndroidManifest.xml` の次のフィールドから取得します。

- **ビルド** – `manifest` ノードの `android:versionCode`
- **名前** - `application` ノードの `android:label`
- **パッケージ名**: `manifest` ノードの `package`
- **バージョン文字列** – `application` ノードの `android:versionName`

# <a name="iostabios"></a>[iOS](#tab/ios)

アプリの情報は、`Info.plist` の次のフィールドから取得します。

- **ビルド** – `CFBundleVersion`
- **名前** -  設定されている場合は `CFBundleDisplayName`、それ以外の場合は `CFBundleName`
- **パッケージ名**: `CFBundleIdentifier`
- **バージョン文字列** – `CFBundleShortVersionString`

# <a name="uwptabuwp"></a>[UWP](#tab/uwp)

アプリの情報は、`Package.appxmanifest` の次のフィールドから取得します。

- **ビルド** – `Identity` ノードの `Version` にある `Build` を使用します
- **名前** -  `Properties` ノードの `DisplayName`
- **パッケージ名**: `Identity` ノードの `Name`
- **バージョン文字列** – `Identity` ノードの `Version`


--------------

## <a name="api"></a>API

- [AppInfo のソース コード](https://github.com/xamarin/Essentials/tree/master/Xamarin.Essentials/AppInfo)
- [AppInfo API のドキュメント](xref:Xamarin.Essentials.AppInfo)

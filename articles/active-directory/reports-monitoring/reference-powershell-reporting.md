---
title: レポート用の Azure AD PowerShell コマンドレット | Microsoft Docs
description: レポート用の Azure AD PowerShell コマンドレットのリファレンス。
services: active-directory
documentationcenter: ''
author: MarkusVi
manager: daveba
editor: ''
ms.assetid: a1f93126-77d1-4345-ab7d-561066041161
ms.service: active-directory
ms.devlang: na
ms.topic: reference
ms.tgt_pltfrm: na
ms.workload: identity
ms.subservice: report-monitor
ms.date: 08/07/2020
ms.author: markvi
ms.reviewer: dhanyahk
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6a198a63d633573ad683a3f8e8215b2975721bc9
ms.sourcegitcommit: c5021f2095e25750eb34fd0b866adf5d81d56c3a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/25/2020
ms.locfileid: "88794935"
---
# <a name="azure-ad-powershell-cmdlets-for-reporting"></a>レポート用の Azure AD PowerShell コマンドレット

> [!NOTE] 
> 現時点では、これらの PowerShell コマンドレットは [Azure AD プレビュー](https://docs.microsoft.com/powershell/module/azuread/?view=azureadps-2.0-preview#directory_auditing) モジュールでのみ使用できます。 プレビュー モジュールは運用環境では推奨されないことに注意してください。 

パブリック プレビュー リリースをインストールするには、以下を使用します。 

```powershell
Install-module AzureADPreview
```

PowerShell を使用して Azure AD に接続する方法の詳細については、[Azure AD PowerShell for Graph](https://docs.microsoft.com/powershell/azure/active-directory/install-adv2?view=azureadps-2.0) に関する記事を参照してください。  

Azure Active Directory (Azure AD) レポートを使用すると、自分の方向のすべての書き込み操作 (監査ログ) および認証データ (サインイン ログ) に関するアクティビティの詳細を取得できます。 この情報は MS Graph API を使用して入手できますが、レポート用の Azure AD PowerShell コマンドレットを使用して、同じデータを取得できるようになりました。

この記事では、監査ログとサインイン ログに使用する PowerShell コマンドレットの概要について説明します。

## <a name="audit-logs"></a>監査ログ

[監査ログ](concept-audit-logs.md)は、Azure AD 内のさまざまな機能によって実行されたすべての変更のログを通して追跡可能性を提供します。 監査ログの例として、ユーザー、アプリ、グループ、ロール、ポリシーの追加や削除など、Azure AD 内のあらゆるリソースに加えられた変更があります。

監査ログへのアクセスは、`Get-AzureADAuditDirectoryLogs コマンドレットを使用して取得します。


| シナリオ                      | PowerShell コマンド |
| :--                           | :--                |
| アプリケーション表示名      | Get-AzureADAuditDirectoryLogs -Filter "initiatedBy/app/displayName eq 'Azure AD Cloud Sync'" |
| カテゴリ                      | Get-AzureADAuditDirectoryLogs -Filter "category eq 'ApplicationManagement'" |
| アクティビティの日付と時刻            | Get-AzureADAuditDirectoryLogs -Filter "activityDateTime gt 2019-04-18" |
| 上記のすべて              | Get-AzureADAuditDirectoryLogs -Filter "initiatedBy/app/displayName eq 'Azure AD Cloud Sync' and category eq 'ApplicationManagement' and activityDateTime gt 2019-04-18"|


次の図は、このコマンドの例を示しています。 

![[Data Summary]\(データの概要\) ボタン](./media/reference-powershell-reporting/get-azureadauditdirectorylogs.png)



## <a name="sign-in-logs"></a>サインイン ログ

[サインイン](concept-sign-ins.md) ログは、マネージド アプリケーションの使用状況とユーザー サインイン アクティビティに関する情報を提供します。

サインイン ログへのアクセスは、`Get-AzureADAuditSignInLogs コマンドレットを使用して取得します。


| シナリオ                      | PowerShell コマンド |
| :--                           | :--                |
| ユーザー表示名             | Get-AzureADAuditSignInLogs -Filter "userDisplayName eq 'Timothy Perkins'" |
| 作成の日付と時刻              | Get-AzureADAuditSignInLogs -Filter "createdDateTime gt 2019-04-18T17:30:00.0Z" (Everything since 5:30 pm on 4/18) |
| Status                        | Get-AzureADAuditSignInLogs -Filter "status/errorCode eq 50105" |
| アプリケーション表示名      | Get-AzureADAuditSignInLogs -Filter "appDisplayName eq 'StoreFrontStudio [wsfed enabled]'" |
| 上記のすべて              | Get-AzureADAuditSignInLogs -Filter "userDisplayName eq 'Timothy Perkins' and status/errorCode ne 0 and appDisplayName eq 'StoreFrontStudio [wsfed enabled]'" |


次の図は、このコマンドの例を示しています。 

![[Data Summary]\(データの概要\) ボタン](./media/reference-powershell-reporting/get-azureadauditsigninlogs.png)



## <a name="next-steps"></a>次のステップ

- [Azure AD レポートの概要](overview-reports.md)
- [監査ログ レポート](concept-audit-logs.md) 
- [Azure AD レポートへのプログラムによるアクセス](concept-reporting-api.md)

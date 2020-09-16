---
ms.openlocfilehash: 9fd4e570d9476f5ac4c310759113d72b354a3060
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606868"
---
### <a name="tls-1x-by-default-passes-the-sch_send_aux_record-flag-to-the-underlying-schannel-api"></a><span data-ttu-id="06b8d-101">TLS 1.x passe par défaut l’indicateur SCH_SEND_AUX_RECORD à l’API SCHANNEL sous-jacente</span><span class="sxs-lookup"><span data-stu-id="06b8d-101">TLS 1.x by default passes the SCH_SEND_AUX_RECORD flag to the underlying SCHANNEL API</span></span>

#### <a name="details"></a><span data-ttu-id="06b8d-102">Détails</span><span class="sxs-lookup"><span data-stu-id="06b8d-102">Details</span></span>

<span data-ttu-id="06b8d-103">Quand vous utilisez TLS 1.x, le .NET Framework s’appuie sur l’API SCHANNEL Windows sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="06b8d-103">When using TLS 1.x, the .NET Framework relies on the underlying Windows SCHANNEL API.</span></span> <span data-ttu-id="06b8d-104">À compter de .NET Framework 4.6, l’indicateur [SCH_SEND_AUX_RECORD](/windows/win32/api/schannel/ns-schannel-schannel_cred) est passé par défaut à SCHANNEL.</span><span class="sxs-lookup"><span data-stu-id="06b8d-104">Starting with .NET Framework 4.6, the [SCH_SEND_AUX_RECORD](/windows/win32/api/schannel/ns-schannel-schannel_cred) flag is passed by default to SCHANNEL.</span></span> <span data-ttu-id="06b8d-105">Cela amène SCHANNEL à fractionner les données à chiffrer en deux enregistrements distincts, le premier sous forme d’un octet unique et le second sous forme de <em>n</em>-1 octets. Dans de rares cas, cela interrompt la communication entre les clients et les serveurs existants qui supposent que les données résident dans un seul enregistrement.</span><span class="sxs-lookup"><span data-stu-id="06b8d-105">This causes SCHANNEL to split data to be encrypted into two separate records, the first as a single byte and the second as <em>n</em>-1 bytes.In rare cases, this breaks communication between clients and existing servers that make the assumption that the data resides in a single record.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="06b8d-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="06b8d-106">Suggestion</span></span>

<span data-ttu-id="06b8d-107">Si ce changement interrompt la communication avec un serveur existant, vous pouvez désactiver l’envoi de l’indicateur [SCH_SEND_AUX_RECORD](/windows/win32/api/schannel/ns-schannel-schannel_cred) et restaurer le comportement précédent qui ne divise pas les données en enregistrements distincts en ajoutant le commutateur suivant à l’élément [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) de la section [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) du fichier de configuration de votre application :</span><span class="sxs-lookup"><span data-stu-id="06b8d-107">If this change breaks communication with an existing server, you can disable sending the [SCH_SEND_AUX_RECORD](/windows/win32/api/schannel/ns-schannel-schannel_cred) flag and restore the previous behavior of not splitting data into separate records by adding the following switch to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app configuration file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchSendAuxRecord=true" />
</runtime>
```

> [!IMPORTANT]
> <span data-ttu-id="06b8d-108">Ce paramètre est fourni dans le seul but d’assurer la compatibilité descendante.</span><span class="sxs-lookup"><span data-stu-id="06b8d-108">This setting is provided for backward compatibility only.</span></span> <span data-ttu-id="06b8d-109">Son utilisation à d’autres fins n’est pas recommandée.</span><span class="sxs-lookup"><span data-stu-id="06b8d-109">Its use is otherwise not recommended.</span></span>

| <span data-ttu-id="06b8d-110">Name</span><span class="sxs-lookup"><span data-stu-id="06b8d-110">Name</span></span>    | <span data-ttu-id="06b8d-111">Valeur</span><span class="sxs-lookup"><span data-stu-id="06b8d-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="06b8d-112">Étendue</span><span class="sxs-lookup"><span data-stu-id="06b8d-112">Scope</span></span>   | <span data-ttu-id="06b8d-113">Edge</span><span class="sxs-lookup"><span data-stu-id="06b8d-113">Edge</span></span>        |
| <span data-ttu-id="06b8d-114">Version</span><span class="sxs-lookup"><span data-stu-id="06b8d-114">Version</span></span> | <span data-ttu-id="06b8d-115">4.6</span><span class="sxs-lookup"><span data-stu-id="06b8d-115">4.6</span></span>         |
| <span data-ttu-id="06b8d-116">Type</span><span class="sxs-lookup"><span data-stu-id="06b8d-116">Type</span></span>    | <span data-ttu-id="06b8d-117">Reciblage</span><span class="sxs-lookup"><span data-stu-id="06b8d-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="06b8d-118">API affectées</span><span class="sxs-lookup"><span data-stu-id="06b8d-118">Affected APIs</span></span>

- <xref:System.Net.Security.SslStream?displayProperty=nameWithType>
- <xref:System.Net.ServicePointManager?displayProperty=nameWithType>
- <xref:System.Net.Http.HttpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>
- <xref:System.Net.FtpWebRequest?displayProperty=nameWithType>

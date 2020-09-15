---
ms.openlocfilehash: 7766a59131fffe2b436c15a5ff58e67001be7941
ms.sourcegitcommit: a69d548f90a03e105ee6701236c38390ecd9ccd1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2020
ms.locfileid: "90065099"
---
### <a name="cryptostreamdispose-transforms-final-block-only-when-writing"></a><span data-ttu-id="00601-101">CryptoStream. dispose transforme le bloc final uniquement lors de l’écriture</span><span class="sxs-lookup"><span data-stu-id="00601-101">CryptoStream.Dispose transforms final block only when writing</span></span>

<span data-ttu-id="00601-102">La <xref:System.Security.Cryptography.CryptoStream.Dispose%2A?displayProperty=nameWithType> méthode, qui est utilisée pour terminer les `CryptoStream` opérations, ne tente plus de transformer le bloc final lors de la lecture.</span><span class="sxs-lookup"><span data-stu-id="00601-102">The <xref:System.Security.Cryptography.CryptoStream.Dispose%2A?displayProperty=nameWithType> method, which is used to finish `CryptoStream` operations, no longer attempts to transform the final block when reading.</span></span>

#### <a name="change-description"></a><span data-ttu-id="00601-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="00601-103">Change description</span></span>

<span data-ttu-id="00601-104">Dans les versions précédentes de .NET, si un utilisateur effectuait une lecture incomplète lors de l’utilisation <xref:System.Security.Cryptography.CryptoStream> de en <xref:System.Security.Cryptography.CryptoStreamMode.Read> mode, la <xref:System.Security.Cryptography.CryptoStream.Dispose%2A> méthode pourrait lever une exception (par exemple, lors de l’utilisation d’AES avec un remplissage).</span><span class="sxs-lookup"><span data-stu-id="00601-104">In previous .NET versions, if a user performed an incomplete read when using <xref:System.Security.Cryptography.CryptoStream> in <xref:System.Security.Cryptography.CryptoStreamMode.Read> mode, the <xref:System.Security.Cryptography.CryptoStream.Dispose%2A> method could throw an exception (for example, when using AES with padding).</span></span> <span data-ttu-id="00601-105">L’exception a été levée, car le dernier bloc a été tenté d’être transformé, mais les données étaient incomplètes.</span><span class="sxs-lookup"><span data-stu-id="00601-105">The exception was thrown because the final block was attempted to be transformed but the data was incomplete.</span></span>

<span data-ttu-id="00601-106">Dans .NET Core 3,0 et versions ultérieures, <xref:System.Security.Cryptography.CryptoStream.Dispose%2A> ne tente plus de transformer le bloc final lors de la lecture, ce qui permet des lectures incomplètes.</span><span class="sxs-lookup"><span data-stu-id="00601-106">In .NET Core 3.0 and later versions, <xref:System.Security.Cryptography.CryptoStream.Dispose%2A> no longer tries to transform the final block when reading, which allows for incomplete reads.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="00601-107">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="00601-107">Reason for change</span></span>

<span data-ttu-id="00601-108">Cette modification active les lectures incomplètes à partir du flux de chiffrement lors de l’annulation d’une opération réseau, sans qu’il soit nécessaire d’intercepter une exception.</span><span class="sxs-lookup"><span data-stu-id="00601-108">This change enables incomplete reads from the crypto stream when a network operation is cancelled, without the need to catch an exception.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="00601-109">Version introduite</span><span class="sxs-lookup"><span data-stu-id="00601-109">Version introduced</span></span>

<span data-ttu-id="00601-110">3.0</span><span class="sxs-lookup"><span data-stu-id="00601-110">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="00601-111">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="00601-111">Recommended action</span></span>

<span data-ttu-id="00601-112">La plupart des applications ne doivent pas être affectées par cette modification.</span><span class="sxs-lookup"><span data-stu-id="00601-112">Most apps should not be affected by this change.</span></span>

<span data-ttu-id="00601-113">Si votre application a déjà intercepté une exception en cas de lecture incomplète, vous pouvez supprimer ce `catch` bloc.</span><span class="sxs-lookup"><span data-stu-id="00601-113">If your application previously caught an exception in case of an incomplete read, you can delete that `catch` block.</span></span>
<span data-ttu-id="00601-114">Si votre application a utilisé la transformation du bloc final dans des scénarios de hachage, vous devrez peut-être vous assurer que le flux entier est lu avant d’être supprimé.</span><span class="sxs-lookup"><span data-stu-id="00601-114">If your app used transforming of the final block in hashing scenarios, you might need to ensure that the entire stream is read before it's disposed.</span></span>

#### <a name="category"></a><span data-ttu-id="00601-115">Category</span><span class="sxs-lookup"><span data-stu-id="00601-115">Category</span></span>

<span data-ttu-id="00601-116">Chiffrement</span><span class="sxs-lookup"><span data-stu-id="00601-116">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="00601-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="00601-117">Affected APIs</span></span>

- <xref:System.Security.Cryptography.CryptoStream.Dispose%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Security.Cryptography.CryptoStream.Dispose`

-->

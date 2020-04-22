---
ms.openlocfilehash: 843c78bb4e4f88d9ac58308a91ab8278364c9580
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021568"
---
### <a name="net-core-30-follows-unicode-best-practices-when-replacing-ill-formed-utf-8-byte-sequences"></a><span data-ttu-id="7bd8a-101">.NET Core 3.0 suit les meilleures pratiques d’Unicode lors du remplacement des séquences de byte UTF-8 mal formées</span><span class="sxs-lookup"><span data-stu-id="7bd8a-101">.NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences</span></span>

<span data-ttu-id="7bd8a-102">Lorsque <xref:System.Text.UTF8Encoding> la classe rencontre une séquence d’ente UTF-8 mal formée au cours d’une opération de transcodage d’au-dessus du caractère, elle remplacera cette séquence par un caractère « ' ' ( U-FFFD REPLACEMENT CHARACTER) dans la chaîne de sortie.</span><span class="sxs-lookup"><span data-stu-id="7bd8a-102">When the <xref:System.Text.UTF8Encoding> class encounters an ill-formed UTF-8 byte sequence during a byte-to-character transcoding operation, it will replace that sequence with a '�' (U+FFFD REPLACEMENT CHARACTER) character in the output string.</span></span> <span data-ttu-id="7bd8a-103">.NET Core 3.0 diffère des versions précédentes de .NET Core et du .NET Framework en suivant les meilleures pratiques d’Unicode pour effectuer ce remplacement pendant l’opération de transcodage.</span><span class="sxs-lookup"><span data-stu-id="7bd8a-103">.NET Core 3.0 differs from previous versions of .NET Core and the .NET Framework by following the Unicode best practice for performing this replacement during the transcoding operation.</span></span>

<span data-ttu-id="7bd8a-104">Cela fait partie d’un effort plus vaste pour améliorer la manipulation <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> <xref:System.Text.Rune?displayProperty=nameWithType> UTF-8 tout au long de .NET, y compris par le nouveau et les types.</span><span class="sxs-lookup"><span data-stu-id="7bd8a-104">This is part of a larger effort to improve UTF-8 handling throughout .NET, including by the new <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> and <xref:System.Text.Rune?displayProperty=nameWithType> types.</span></span> <span data-ttu-id="7bd8a-105">Le <xref:System.Text.UTF8Encoding> type a été donné la mécanique améliorée de manipulation d’erreur de sorte qu’il produit la sortie compatible avec les types nouvellement introduits.</span><span class="sxs-lookup"><span data-stu-id="7bd8a-105">The <xref:System.Text.UTF8Encoding> type was given improved error handling mechanics so that it produces output consistent with the newly introduced types.</span></span>

#### <a name="change-description"></a><span data-ttu-id="7bd8a-106">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="7bd8a-106">Change description</span></span>

<span data-ttu-id="7bd8a-107">En commençant par .NET Core 3.0, lorsque <xref:System.Text.UTF8Encoding> les octets transcontéraux vers des personnages, la classe effectue la substitution de caractères basée sur les meilleures pratiques Unicode.</span><span class="sxs-lookup"><span data-stu-id="7bd8a-107">Starting with .NET Core 3.0, when transcoding bytes to characters, the <xref:System.Text.UTF8Encoding> class performs character substitution based on Unicode best practices.</span></span> <span data-ttu-id="7bd8a-108">Le mécanisme de substitution utilisé est décrit par [The Unicode Standard, Version 12.0, Sec. 3.9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) dans le titre intitulé _U-FFFD Substitution of Maximal Subparts_.</span><span class="sxs-lookup"><span data-stu-id="7bd8a-108">The substitution mechanism used is described by [The Unicode Standard, Version 12.0, Sec. 3.9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) in the heading titled _U+FFFD Substitution of Maximal Subparts_.</span></span>

<span data-ttu-id="7bd8a-109">Ce comportement ne s’applique _que_ lorsque la séquence d’entrées byte contient des données UTF-8 mal formées.</span><span class="sxs-lookup"><span data-stu-id="7bd8a-109">This behavior _only_ applies when the input byte sequence contains ill-formed UTF-8 data.</span></span> <span data-ttu-id="7bd8a-110">En outre, <xref:System.Text.UTF8Encoding> si l’instance a été construite avec `throwOnInvalidBytes: true` (voir la<xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>documentation `UTF8Encoding` [UTF8Encoding constructor](, l’instance continuera à jeter sur l’entrée invalide plutôt que d’effectuer le remplacement U -FFFD.</span><span class="sxs-lookup"><span data-stu-id="7bd8a-110">Additionally, if the <xref:System.Text.UTF8Encoding> instance has been constructed with `throwOnInvalidBytes: true` (see the [UTF8Encoding constructor documentation](<xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>, the `UTF8Encoding` instance will continue to throw on invalid input rather than perform U+FFFD replacement.</span></span>

<span data-ttu-id="7bd8a-111">Ce qui suit illustre l’impact de ce changement avec une entrée invalide de 3 ans :</span><span class="sxs-lookup"><span data-stu-id="7bd8a-111">The following illustrates the impact of this change with an invalid 3-byte input:</span></span>

|<span data-ttu-id="7bd8a-112">Entrée 3-byte mal formée</span><span class="sxs-lookup"><span data-stu-id="7bd8a-112">Ill-formed 3-byte input</span></span>|<span data-ttu-id="7bd8a-113">Sortie avant .NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="7bd8a-113">Output before .NET Core 3.0</span></span>|<span data-ttu-id="7bd8a-114">Sortie à partir de .NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="7bd8a-114">Output starting with .NET Core 3.0</span></span>|
|---|---|---|
| `[ ED A0 90 ]` | <span data-ttu-id="7bd8a-115">`[ FFFD FFFD ]`(sortie de 2 caractères)</span><span class="sxs-lookup"><span data-stu-id="7bd8a-115">`[ FFFD FFFD ]` (2-character output)</span></span>| <span data-ttu-id="7bd8a-116">`[ FFFD FFFD FFFD ]`(sortie de 3 caractères)</span><span class="sxs-lookup"><span data-stu-id="7bd8a-116">`[ FFFD FFFD FFFD ]` (3-character output)</span></span>|

<span data-ttu-id="7bd8a-117">Cette sortie 3-char est la sortie préférée, selon _le tableau 3-9_ de l’Unicode Standard PDF précédemment lié.</span><span class="sxs-lookup"><span data-stu-id="7bd8a-117">This 3-char output is the preferred output, according to _Table 3-9_ of the previously linked Unicode Standard PDF.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="7bd8a-118">Version introduite</span><span class="sxs-lookup"><span data-stu-id="7bd8a-118">Version introduced</span></span>

<span data-ttu-id="7bd8a-119">3.0</span><span class="sxs-lookup"><span data-stu-id="7bd8a-119">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7bd8a-120">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="7bd8a-120">Recommended action</span></span>

<span data-ttu-id="7bd8a-121">Aucune action n’est requise de la part du développeur.</span><span class="sxs-lookup"><span data-stu-id="7bd8a-121">No action is required on the part of the developer.</span></span>

#### <a name="category"></a><span data-ttu-id="7bd8a-122">Category</span><span class="sxs-lookup"><span data-stu-id="7bd8a-122">Category</span></span>

<span data-ttu-id="7bd8a-123">Core .NET bibliothèques</span><span class="sxs-lookup"><span data-stu-id="7bd8a-123">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7bd8a-124">API affectées</span><span class="sxs-lookup"><span data-stu-id="7bd8a-124">Affected APIs</span></span>

- <xref:System.Text.UTF8Encoding.GetCharCount%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetChars%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Text.UTF8Encoding.GetCharCount`
- `Overload:System.Text.UTF8Encoding.GetChars`
- `M:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)`

-->

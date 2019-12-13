---
ms.openlocfilehash: db1d09c8c9e606b5327a42977a74a74703282d84
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568117"
---
### <a name="net-core-30-follows-unicode-best-practices-when-replacing-ill-formed-utf-8-byte-sequences"></a><span data-ttu-id="4a938-101">.NET Core 3,0 suit les meilleures pratiques Unicode lors du remplacement de séquences d’octets UTF-8 incorrectes</span><span class="sxs-lookup"><span data-stu-id="4a938-101">.NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences</span></span>

<span data-ttu-id="4a938-102">Lorsque la classe <xref:System.Text.UTF8Encoding> rencontre une séquence d’octets UTF-8 incorrecte lors d’une opération de transcodage octet-à-caractère, elle remplace cette séquence par un caractère «» (caractère de remplacement U + FFFD) dans la chaîne de sortie.</span><span class="sxs-lookup"><span data-stu-id="4a938-102">When the <xref:System.Text.UTF8Encoding> class encounters an ill-formed UTF-8 byte sequence during a byte-to-character transcoding operation, it will replace that sequence with a '�' (U+FFFD REPLACEMENT CHARACTER) character in the output string.</span></span> <span data-ttu-id="4a938-103">.NET Core 3,0 diffère des versions précédentes de .NET Core et du .NET Framework en suivant la meilleure pratique Unicode pour effectuer ce remplacement pendant l’opération de transcodage.</span><span class="sxs-lookup"><span data-stu-id="4a938-103">.NET Core 3.0 differs from previous versions of .NET Core and the .NET Framework by following the Unicode best practice for performing this replacement during the transcoding operation.</span></span>

<span data-ttu-id="4a938-104">Cela fait partie d’un effort plus important pour améliorer la gestion d’UTF-8 dans .NET, y compris par les nouveaux types de <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> et de <xref:System.Text.Rune?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4a938-104">This is part of a larger effort to improve UTF-8 handling throughout .NET, including by the new <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> and <xref:System.Text.Rune?displayProperty=nameWithType> types.</span></span> <span data-ttu-id="4a938-105">Le type de <xref:System.Text.UTF8Encoding> a obtenu des mécanismes améliorés de gestion des erreurs afin de produire une sortie cohérente avec les types nouvellement introduits.</span><span class="sxs-lookup"><span data-stu-id="4a938-105">The <xref:System.Text.UTF8Encoding> type was given improved error handling mechanics so that it produces output consistent with the newly introduced types.</span></span>

#### <a name="change-description"></a><span data-ttu-id="4a938-106">Modifier la description</span><span class="sxs-lookup"><span data-stu-id="4a938-106">Change description</span></span>

<span data-ttu-id="4a938-107">À compter de .NET Core 3,0, lors du transcodage d’octets en caractères, la classe <xref:System.Text.UTF8Encoding> effectue une substitution de caractères basée sur les meilleures pratiques Unicode.</span><span class="sxs-lookup"><span data-stu-id="4a938-107">Starting with .NET Core 3.0, when transcoding bytes to characters, the <xref:System.Text.UTF8Encoding> class performs character substitution based on Unicode best practices.</span></span> <span data-ttu-id="4a938-108">Le mécanisme de substitution utilisé est décrit par [la norme Unicode, Version 12,0, sec. 3,9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) dans l’en-tête intitulé _U + FFFD substitution of maximum subpartments_.</span><span class="sxs-lookup"><span data-stu-id="4a938-108">The substitution mechanism used is described by [The Unicode Standard, Version 12.0, Sec. 3.9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) in the heading titled _U+FFFD Substitution of Maximal Subparts_.</span></span>

<span data-ttu-id="4a938-109">Ce comportement s’applique _uniquement_ lorsque la séquence d’octets en entrée contient des données UTF-8 incorrectes.</span><span class="sxs-lookup"><span data-stu-id="4a938-109">This behavior _only_ applies when the input byte sequence contains ill-formed UTF-8 data.</span></span> <span data-ttu-id="4a938-110">En outre, si l’instance <xref:System.Text.UTF8Encoding> a été construite avec `throwOnInvalidBytes: true` (consultez la [documentation du constructeur UTF8Encoding] (<xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>, l’instance `UTF8Encoding` continuera à lever sur une entrée non valide plutôt que d’effectuer un remplacement U + FFFD.</span><span class="sxs-lookup"><span data-stu-id="4a938-110">Additionally, if the <xref:System.Text.UTF8Encoding> instance has been constructed with `throwOnInvalidBytes: true` (see the [UTF8Encoding constructor documentation](<xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>, the `UTF8Encoding` instance will continue to throw on invalid input rather than perform U+FFFD replacement.</span></span>

<span data-ttu-id="4a938-111">L’exemple suivant illustre l’impact de cette modification avec une entrée non valide de 3 octets :</span><span class="sxs-lookup"><span data-stu-id="4a938-111">The following illustrates the impact of this change with an invalid 3-byte input:</span></span>

|<span data-ttu-id="4a938-112">Entrée de 3 octets incorrecte</span><span class="sxs-lookup"><span data-stu-id="4a938-112">Ill-formed 3-byte input</span></span>|<span data-ttu-id="4a938-113">Sortie avant .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="4a938-113">Output before .NET Core 3.0</span></span>|<span data-ttu-id="4a938-114">Sortie à partir de .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="4a938-114">Output starting with .NET Core 3.0</span></span>|
|---|---|---|
| `[ ED A0 90 ]` | <span data-ttu-id="4a938-115">`[ FFFD FFFD ]` (sortie à 2 caractères)</span><span class="sxs-lookup"><span data-stu-id="4a938-115">`[ FFFD FFFD ]` (2-character output)</span></span>| <span data-ttu-id="4a938-116">`[ FFFD FFFD FFFD ]` (sortie à 3 caractères)</span><span class="sxs-lookup"><span data-stu-id="4a938-116">`[ FFFD FFFD FFFD ]` (3-character output)</span></span>|

<span data-ttu-id="4a938-117">Cette sortie de 3 caractères est la sortie par défaut, selon la _Table 3-9_ du fichier PDF standard Unicode lié précédemment.</span><span class="sxs-lookup"><span data-stu-id="4a938-117">This 3-char output is the preferred output, according to _Table 3-9_ of the previously linked Unicode Standard PDF.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="4a938-118">Version introduite</span><span class="sxs-lookup"><span data-stu-id="4a938-118">Version introduced</span></span>

<span data-ttu-id="4a938-119">3.0</span><span class="sxs-lookup"><span data-stu-id="4a938-119">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4a938-120">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="4a938-120">Recommended action</span></span>

<span data-ttu-id="4a938-121">Aucune action n’est requise de la part du développeur.</span><span class="sxs-lookup"><span data-stu-id="4a938-121">No action is required on the part of the developer.</span></span>

#### <a name="category"></a><span data-ttu-id="4a938-122">Catégorie</span><span class="sxs-lookup"><span data-stu-id="4a938-122">Category</span></span>

<span data-ttu-id="4a938-123">CoreFx</span><span class="sxs-lookup"><span data-stu-id="4a938-123">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4a938-124">API affectées</span><span class="sxs-lookup"><span data-stu-id="4a938-124">Affected APIs</span></span>

- <xref:System.Text.UTF8Encoding.GetCharCount%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetChars%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Text.UTF8Encoding.GetCharCount`
- `Overload:System.Text.UTF8Encoding.GetChars`
- `M:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)`

-->

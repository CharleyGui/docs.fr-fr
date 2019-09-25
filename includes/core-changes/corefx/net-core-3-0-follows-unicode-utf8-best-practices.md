---
ms.openlocfilehash: 0795ee244bf3d1261bbe61dc0c67c3936f427f04
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216350"
---
### <a name="net-core-30-follows-unicode-best-practices-when-replacing-ill-formed-utf-8-byte-sequences"></a><span data-ttu-id="b0f46-101">.NET Core 3,0 suit les meilleures pratiques Unicode lors du remplacement de séquences d’octets UTF-8 incorrectes</span><span class="sxs-lookup"><span data-stu-id="b0f46-101">.NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences</span></span>

<span data-ttu-id="b0f46-102">Quand la <xref:System.Text.UTF8Encoding> classe rencontre une séquence d’octets UTF-8 incorrecte lors d’une opération de transcodage d’un octet à un caractère, elle remplace cette séquence par un caractère de remplacement «» (caractère de remplacement U + FFFD) dans la chaîne de sortie.</span><span class="sxs-lookup"><span data-stu-id="b0f46-102">When the <xref:System.Text.UTF8Encoding> class encounters an ill-formed UTF-8 byte sequence during a byte-to-character transcoding operation, it will replace that sequence with a '�' (U+FFFD REPLACEMENT CHARACTER) character in the output string.</span></span> <span data-ttu-id="b0f46-103">.NET Core 3,0 diffère des versions précédentes de .NET Core et du .NET Framework en suivant la meilleure pratique Unicode pour effectuer ce remplacement pendant l’opération de transcodage.</span><span class="sxs-lookup"><span data-stu-id="b0f46-103">.NET Core 3.0 differs from previous versions of .NET Core and the .NET Framework by following the Unicode best practice for performing this replacement during the transcoding operation.</span></span>

<span data-ttu-id="b0f46-104">Cela fait partie d’un effort plus important pour améliorer la gestion d’UTF-8 dans .net, y <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> compris <xref:System.Text.Rune?displayProperty=nameWithType> par les nouveaux types et.</span><span class="sxs-lookup"><span data-stu-id="b0f46-104">This is part of a larger effort to improve UTF-8 handling throughout .NET, including by the new <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> and <xref:System.Text.Rune?displayProperty=nameWithType> types.</span></span> <span data-ttu-id="b0f46-105">Le <xref:System.Text.UTF8Encoding> type a été amélioré pour la gestion des erreurs afin de produire une sortie cohérente avec les types nouvellement introduits.</span><span class="sxs-lookup"><span data-stu-id="b0f46-105">The <xref:System.Text.UTF8Encoding> type was given improved error handling mechanics so that it produces output consistent with the newly introduced types.</span></span>

#### <a name="details"></a><span data-ttu-id="b0f46-106">Détails</span><span class="sxs-lookup"><span data-stu-id="b0f46-106">Details</span></span>

<span data-ttu-id="b0f46-107">À compter de .net Core 3,0, lors du transcodage d’octets en <xref:System.Text.UTF8Encoding> caractères, la classe effectue une substitution de caractères basée sur les meilleures pratiques Unicode.</span><span class="sxs-lookup"><span data-stu-id="b0f46-107">Starting with .NET Core 3.0, when transcoding bytes to characters, the <xref:System.Text.UTF8Encoding> class performs character substitution based on Unicode best practices.</span></span> <span data-ttu-id="b0f46-108">Le mécanisme de substitution utilisé est décrit par [la norme Unicode, Version 12,0, sec. 3,9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) dans l’en-tête intitulé _U + FFFD substitution of maximum subpartments_.</span><span class="sxs-lookup"><span data-stu-id="b0f46-108">The substitution mechanism used is described by [The Unicode Standard, Version 12.0, Sec. 3.9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) in the heading titled _U+FFFD Substitution of Maximal Subparts_.</span></span>

<span data-ttu-id="b0f46-109">Ce comportement s’applique _uniquement_ lorsque la séquence d’octets en entrée contient des données UTF-8 incorrectes.</span><span class="sxs-lookup"><span data-stu-id="b0f46-109">This behavior _only_ applies when the input byte sequence contains ill-formed UTF-8 data.</span></span> <span data-ttu-id="b0f46-110">En outre, si l' <xref:System.Text.UTF8Encoding> instance a été construite avec `throwOnInvalidBytes: true` (consultez la [documentation du constructeur UTF8Encoding]<xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>(, `UTF8Encoding` l’instance continuera à lever sur une entrée non valide plutôt que d’exécuter U + FFFD nouveau.</span><span class="sxs-lookup"><span data-stu-id="b0f46-110">Additionally, if the <xref:System.Text.UTF8Encoding> instance has been constructed with `throwOnInvalidBytes: true` (see the [UTF8Encoding constructor documentation](<xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>, the `UTF8Encoding` instance will continue to throw on invalid input rather than perform U+FFFD replacement.</span></span>

<span data-ttu-id="b0f46-111">L’exemple suivant illustre l’impact de cette modification avec une entrée non valide de 3 octets :</span><span class="sxs-lookup"><span data-stu-id="b0f46-111">The following illustrates the impact of this change with an invalid 3-byte input:</span></span>

|<span data-ttu-id="b0f46-112">Entrée de 3 octets incorrecte</span><span class="sxs-lookup"><span data-stu-id="b0f46-112">Ill-formed 3-byte input</span></span>|<span data-ttu-id="b0f46-113">Sortie avant .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="b0f46-113">Output before .NET Core 3.0</span></span>|<span data-ttu-id="b0f46-114">Sortie à partir de .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="b0f46-114">Output starting with .NET Core 3.0</span></span>|
|---|---|---|
| `[ ED A0 90 ]` | <span data-ttu-id="b0f46-115">`[ FFFD FFFD ]`(sortie à 2 caractères)</span><span class="sxs-lookup"><span data-stu-id="b0f46-115">`[ FFFD FFFD ]` (2-character output)</span></span>| <span data-ttu-id="b0f46-116">`[ FFFD FFFD FFFD ]`(sortie à 3 caractères)</span><span class="sxs-lookup"><span data-stu-id="b0f46-116">`[ FFFD FFFD FFFD ]` (3-character output)</span></span>|

<span data-ttu-id="b0f46-117">Cette sortie de 3 caractères est la sortie par défaut, selon la _Table 3-9_ du fichier PDF standard Unicode lié précédemment.</span><span class="sxs-lookup"><span data-stu-id="b0f46-117">This 3-char output is the preferred output, according to _Table 3-9_ of the previously linked Unicode Standard PDF.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b0f46-118">Version introduite</span><span class="sxs-lookup"><span data-stu-id="b0f46-118">Version introduced</span></span>

<span data-ttu-id="b0f46-119">3.0</span><span class="sxs-lookup"><span data-stu-id="b0f46-119">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b0f46-120">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="b0f46-120">Recommended action</span></span>

<span data-ttu-id="b0f46-121">Aucune action n’est requise de la part du développeur.</span><span class="sxs-lookup"><span data-stu-id="b0f46-121">No action is required on the part of the developer.</span></span>

#### <a name="category"></a><span data-ttu-id="b0f46-122">Category</span><span class="sxs-lookup"><span data-stu-id="b0f46-122">Category</span></span>

<span data-ttu-id="b0f46-123">CoreFx</span><span class="sxs-lookup"><span data-stu-id="b0f46-123">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b0f46-124">API affectées</span><span class="sxs-lookup"><span data-stu-id="b0f46-124">Affected APIs</span></span>

- <xref:System.Text.UTF8Encoding.GetCharCount%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetChars%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Text.UTF8Encoding.GetCharCount`
- `Overload:System.Text.UTF8Encoding.GetChars`
- `M:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)`

-->

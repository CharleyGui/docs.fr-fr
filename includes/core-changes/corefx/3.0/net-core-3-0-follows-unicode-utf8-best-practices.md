---
ms.openlocfilehash: 298cb441bf9fe7daddb30c85f9d7366dc972628c
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721624"
---
### <a name="replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines"></a><span data-ttu-id="206e1-101">Le remplacement des séquences d’octets UTF-8 incorrectes suit les instructions Unicode</span><span class="sxs-lookup"><span data-stu-id="206e1-101">Replacing ill-formed UTF-8 byte sequences follows Unicode guidelines</span></span>

<span data-ttu-id="206e1-102">Quand la <xref:System.Text.UTF8Encoding> classe rencontre une séquence d’octets UTF-8 incorrecte lors d’une opération de transcodage d’un octet à un caractère, elle remplace cette séquence par un caractère de remplacement «» (caractère de remplacement U + FFFD) dans la chaîne de sortie.</span><span class="sxs-lookup"><span data-stu-id="206e1-102">When the <xref:System.Text.UTF8Encoding> class encounters an ill-formed UTF-8 byte sequence during a byte-to-character transcoding operation, it replaces that sequence with a '�' (U+FFFD REPLACEMENT CHARACTER) character in the output string.</span></span> <span data-ttu-id="206e1-103">.NET Core 3,0 diffère des versions précédentes de .NET Core et du .NET Framework en suivant la meilleure pratique Unicode pour effectuer ce remplacement pendant l’opération de transcodage.</span><span class="sxs-lookup"><span data-stu-id="206e1-103">.NET Core 3.0 differs from previous versions of .NET Core and the .NET Framework by following the Unicode best practice for performing this replacement during the transcoding operation.</span></span>

<span data-ttu-id="206e1-104">Cela fait partie d’un effort plus important pour améliorer la gestion d’UTF-8 dans .NET, y compris par les nouveaux <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> <xref:System.Text.Rune?displayProperty=nameWithType> types et.</span><span class="sxs-lookup"><span data-stu-id="206e1-104">This is part of a larger effort to improve UTF-8 handling throughout .NET, including by the new <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> and <xref:System.Text.Rune?displayProperty=nameWithType> types.</span></span> <span data-ttu-id="206e1-105">Le <xref:System.Text.UTF8Encoding> type a été amélioré pour la gestion des erreurs afin de produire une sortie cohérente avec les types nouvellement introduits.</span><span class="sxs-lookup"><span data-stu-id="206e1-105">The <xref:System.Text.UTF8Encoding> type was given improved error handling mechanics so that it produces output consistent with the newly introduced types.</span></span>

#### <a name="change-description"></a><span data-ttu-id="206e1-106">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="206e1-106">Change description</span></span>

<span data-ttu-id="206e1-107">À compter de .NET Core 3,0, lors du transcodage d’octets en caractères, la <xref:System.Text.UTF8Encoding> classe effectue une substitution de caractères basée sur les meilleures pratiques Unicode.</span><span class="sxs-lookup"><span data-stu-id="206e1-107">Starting with .NET Core 3.0, when transcoding bytes to characters, the <xref:System.Text.UTF8Encoding> class performs character substitution based on Unicode best practices.</span></span> <span data-ttu-id="206e1-108">Le mécanisme de substitution utilisé est décrit par [la norme Unicode, Version 12,0, sec. 3,9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) dans l’en-tête intitulé _U + FFFD substitution of maximum subpartments_.</span><span class="sxs-lookup"><span data-stu-id="206e1-108">The substitution mechanism used is described by [The Unicode Standard, Version 12.0, Sec. 3.9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) in the heading titled _U+FFFD Substitution of Maximal Subparts_.</span></span>

<span data-ttu-id="206e1-109">Ce comportement s’applique _uniquement_ lorsque la séquence d’octets en entrée contient des données UTF-8 incorrectes.</span><span class="sxs-lookup"><span data-stu-id="206e1-109">This behavior _only_ applies when the input byte sequence contains ill-formed UTF-8 data.</span></span> <span data-ttu-id="206e1-110">En outre, si l' <xref:System.Text.UTF8Encoding> instance a été construite avec `throwOnInvalidBytes: true` , l' `UTF8Encoding` instance continuera à lever sur une entrée non valide plutôt que d’effectuer un remplacement U + FFFD.</span><span class="sxs-lookup"><span data-stu-id="206e1-110">Additionally, if the <xref:System.Text.UTF8Encoding> instance has been constructed with `throwOnInvalidBytes: true`, the `UTF8Encoding` instance will continue to throw on invalid input rather than perform U+FFFD replacement.</span></span> <span data-ttu-id="206e1-111">Pour plus d’informations sur le `UTF8Encoding` constructeur, consultez <xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)> .</span><span class="sxs-lookup"><span data-stu-id="206e1-111">For more information about the `UTF8Encoding` constructor, see <xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>.</span></span>

<span data-ttu-id="206e1-112">Le tableau suivant illustre l’impact de cette modification sur une entrée non valide de 3 octets :</span><span class="sxs-lookup"><span data-stu-id="206e1-112">The following table illustrates the impact of this change with an invalid 3-byte input:</span></span>

| <span data-ttu-id="206e1-113">Entrée de 3 octets incorrecte</span><span class="sxs-lookup"><span data-stu-id="206e1-113">Ill-formed 3-byte input</span></span> | <span data-ttu-id="206e1-114">Sortie avant .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="206e1-114">Output before .NET Core 3.0</span></span>          | <span data-ttu-id="206e1-115">Sortie à partir de .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="206e1-115">Output starting with .NET Core 3.0</span></span>        |
|-------------------------|--------------------------------------|-------------------------------------------|
| `[ ED A0 90 ]`          | <span data-ttu-id="206e1-116">`[ FFFD FFFD ]`(sortie à 2 caractères)</span><span class="sxs-lookup"><span data-stu-id="206e1-116">`[ FFFD FFFD ]` (2-character output)</span></span> | <span data-ttu-id="206e1-117">`[ FFFD FFFD FFFD ]`(sortie à 3 caractères)</span><span class="sxs-lookup"><span data-stu-id="206e1-117">`[ FFFD FFFD FFFD ]` (3-character output)</span></span> |

<span data-ttu-id="206e1-118">La sortie de 3 caractères est la sortie par défaut, selon la _Table 3-9_ du fichier PDF standard Unicode lié précédemment.</span><span class="sxs-lookup"><span data-stu-id="206e1-118">The 3-char output is the preferred output, according to _Table 3-9_ of the previously linked Unicode Standard PDF.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="206e1-119">Version introduite</span><span class="sxs-lookup"><span data-stu-id="206e1-119">Version introduced</span></span>

<span data-ttu-id="206e1-120">3.0</span><span class="sxs-lookup"><span data-stu-id="206e1-120">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="206e1-121">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="206e1-121">Recommended action</span></span>

<span data-ttu-id="206e1-122">Aucune action n’est requise de la part du développeur.</span><span class="sxs-lookup"><span data-stu-id="206e1-122">No action is required on the part of the developer.</span></span>

#### <a name="category"></a><span data-ttu-id="206e1-123">Category</span><span class="sxs-lookup"><span data-stu-id="206e1-123">Category</span></span>

<span data-ttu-id="206e1-124">Bibliothèques .NET Core</span><span class="sxs-lookup"><span data-stu-id="206e1-124">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="206e1-125">API affectées</span><span class="sxs-lookup"><span data-stu-id="206e1-125">Affected APIs</span></span>

- <xref:System.Text.UTF8Encoding.GetCharCount%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetChars%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.UTF8Encoding.GetCharCount`
- `Overload:System.Text.UTF8Encoding.GetChars`
- `M:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)`

-->

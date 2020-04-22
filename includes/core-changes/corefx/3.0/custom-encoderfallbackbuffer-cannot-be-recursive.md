---
ms.openlocfilehash: 820825f0545aa78729414c388385b339225b1235
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021580"
---
### <a name="custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively"></a><span data-ttu-id="f4984-101">Custom EncoderFallbackBuffer instances ne peuvent pas se replier de façon récursive</span><span class="sxs-lookup"><span data-stu-id="f4984-101">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>

<span data-ttu-id="f4984-102">Les <xref:System.Text.EncoderFallbackBuffer> instances personnalisées ne peuvent pas se replier de façon récursive.</span><span class="sxs-lookup"><span data-stu-id="f4984-102">Custom <xref:System.Text.EncoderFallbackBuffer> instances cannot fall back recursively.</span></span> <span data-ttu-id="f4984-103">La mise <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> en œuvre de doit entraîner une séquence de caractères qui est convertible à l’encodage de destination.</span><span class="sxs-lookup"><span data-stu-id="f4984-103">The implementation of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> must result in a character sequence that is convertible to the destination encoding.</span></span> <span data-ttu-id="f4984-104">Sinon, une exception se produit.</span><span class="sxs-lookup"><span data-stu-id="f4984-104">Otherwise, an exception occurs.</span></span>

#### <a name="change-description"></a><span data-ttu-id="f4984-105">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="f4984-105">Change description</span></span>

<span data-ttu-id="f4984-106">Au cours d’une opération de transcodage de caractère à l’autre, le temps d’exécution détecte les <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> séquences UTF-16 mal formées ou non révertisables et fournit ces caractères à la méthode.</span><span class="sxs-lookup"><span data-stu-id="f4984-106">During a character-to-byte transcoding operation, the runtime detects ill-formed or nonconvertible UTF-16 sequences and provides those characters to the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="f4984-107">La `Fallback` méthode détermine quels caractères doivent être substitués aux données originales non <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> convertiables, et ces caractères sont drainés en appelant en boucle.</span><span class="sxs-lookup"><span data-stu-id="f4984-107">The `Fallback` method determines which characters should be substituted for the original nonconvertible data, and these characters are drained by calling <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> in a loop.</span></span>

<span data-ttu-id="f4984-108">Le temps d’exécution tente alors de transcoder ces caractères de substitution au codage cible.</span><span class="sxs-lookup"><span data-stu-id="f4984-108">The runtime then attempts to transcode these substitution characters to the target encoding.</span></span> <span data-ttu-id="f4984-109">Si cette opération réussit, le temps d’exécution continue le transcodage d’où il s’est détaché dans la chaîne d’entrée d’origine.</span><span class="sxs-lookup"><span data-stu-id="f4984-109">If this operation succeeds, the runtime continues transcoding from where it left off in the original input string.</span></span>

<span data-ttu-id="f4984-110">Dans .NET Core Preview 7 et les <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> versions antérieures, les implémentations personnalisées de peuvent retourner des séquences de caractères qui ne sont pas convertibles à l’encodage de destination.</span><span class="sxs-lookup"><span data-stu-id="f4984-110">In .NET Core Preview 7 and earlier versions, custom implementations of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> can return character sequences that are not convertible to the destination encoding.</span></span> <span data-ttu-id="f4984-111">Si les caractères substitués ne peuvent pas être transcodés vers l’encodage cible, le temps d’exécution invoque à nouveau la <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> méthode avec les caractères de substitution, s’attendant à ce que la <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> méthode renvoie une nouvelle séquence de substitution.</span><span class="sxs-lookup"><span data-stu-id="f4984-111">If the substituted characters cannot be transcoded to the target encoding, the runtime invokes the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> method once again with the substitution characters, expecting the <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> method to return a new substitution sequence.</span></span> <span data-ttu-id="f4984-112">Ce processus se poursuit jusqu’à ce que le temps d’exécution voit finalement une substitution décapotable bien formée, ou jusqu’à ce qu’un nombre maximum de récurrence soit atteint.</span><span class="sxs-lookup"><span data-stu-id="f4984-112">This process continues until the runtime eventually sees a well-formed, convertible substitution, or until a maximum recursion count is reached.</span></span>

<span data-ttu-id="f4984-113">En commençant par .NET Core 3.0, implémentations personnalisées de séquences de <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> caractères de retour de must qui sont convertibles à l’encodage de destination.</span><span class="sxs-lookup"><span data-stu-id="f4984-113">Starting with .NET Core 3.0, custom implementations of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> must return character sequences that are convertible to the destination encoding.</span></span> <span data-ttu-id="f4984-114">Si les caractères substitués ne peuvent pas <xref:System.ArgumentException> être transcodés vers l’encodage cible, un est lancé.</span><span class="sxs-lookup"><span data-stu-id="f4984-114">If the substituted characters cannot be transcoded to the target encoding, an <xref:System.ArgumentException> is thrown.</span></span> <span data-ttu-id="f4984-115">Le temps d’exécution ne fera plus <xref:System.Text.EncoderFallbackBuffer> d’appels récursifs dans l’instance.</span><span class="sxs-lookup"><span data-stu-id="f4984-115">The runtime will no longer make recursive calls into the <xref:System.Text.EncoderFallbackBuffer> instance.</span></span>

<span data-ttu-id="f4984-116">Ce comportement ne s’applique que lorsque les trois conditions suivantes sont remplies :</span><span class="sxs-lookup"><span data-stu-id="f4984-116">This behavior only applies when all three of the following conditions are met:</span></span>

- <span data-ttu-id="f4984-117">Le temps d’exécution détecte une séquence UTF-16 mal formée ou une séquence UTF-16 qui ne peut pas être convertie en codage cible.</span><span class="sxs-lookup"><span data-stu-id="f4984-117">The runtime detects an ill-formed UTF-16 sequence or a UTF-16 sequence that cannot be converted to the target encoding.</span></span>
- <span data-ttu-id="f4984-118">Une <xref:System.Text.EncoderFallback> coutume a été spécifiée.</span><span class="sxs-lookup"><span data-stu-id="f4984-118">A custom <xref:System.Text.EncoderFallback> has been specified.</span></span>
- <span data-ttu-id="f4984-119">La <xref:System.Text.EncoderFallback> coutume tente de remplacer une nouvelle séquence UTF-16 mal formée ou non convertie.</span><span class="sxs-lookup"><span data-stu-id="f4984-119">The custom <xref:System.Text.EncoderFallback> attempts to substitute a new ill-formed or nonconvertible UTF-16 sequence.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f4984-120">Version introduite</span><span class="sxs-lookup"><span data-stu-id="f4984-120">Version introduced</span></span>

<span data-ttu-id="f4984-121">3.0</span><span class="sxs-lookup"><span data-stu-id="f4984-121">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f4984-122">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="f4984-122">Recommended action</span></span>

<span data-ttu-id="f4984-123">La plupart des développeurs n’ont pas besoin de prendre aucune mesure.</span><span class="sxs-lookup"><span data-stu-id="f4984-123">Most developers needn't take any action.</span></span>

<span data-ttu-id="f4984-124">Si une application <xref:System.Text.EncoderFallback> utilise <xref:System.Text.EncoderFallbackBuffer> une coutume et <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> une classe, assurez-vous que la mise en œuvre de peuple le <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> tampon de repli avec des données UTF-16 bien formées qui sont directement convertibles au codage cible lorsque la méthode est invoquée pour la première fois par le temps d’exécution.</span><span class="sxs-lookup"><span data-stu-id="f4984-124">If an application uses a custom <xref:System.Text.EncoderFallback> and <xref:System.Text.EncoderFallbackBuffer> class, ensure the implementation of <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> populates the fallback buffer with well-formed UTF-16 data that is directly convertible to the target encoding when the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> method is first invoked by the runtime.</span></span>

#### <a name="category"></a><span data-ttu-id="f4984-125">Category</span><span class="sxs-lookup"><span data-stu-id="f4984-125">Category</span></span>

<span data-ttu-id="f4984-126">Core .NET bibliothèques</span><span class="sxs-lookup"><span data-stu-id="f4984-126">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f4984-127">API affectées</span><span class="sxs-lookup"><span data-stu-id="f4984-127">Affected APIs</span></span>

- <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>
- <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Text.EncoderFallbackBuffer.Fallback`
- `M:System.Text.EncoderFallbackBuffer.GetNextChar`

-->

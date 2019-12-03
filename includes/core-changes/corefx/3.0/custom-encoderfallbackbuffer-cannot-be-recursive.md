---
ms.openlocfilehash: 58d1c8cd3aff52703522391c14348bd81c108587
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568138"
---
### <a name="custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively"></a><span data-ttu-id="6dcb4-101">Les instances EncoderFallbackBuffer personnalisées ne peuvent pas être rétablies de manière récursive</span><span class="sxs-lookup"><span data-stu-id="6dcb4-101">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>

<span data-ttu-id="6dcb4-102">Les instances de <xref:System.Text.EncoderFallbackBuffer> personnalisées ne peuvent pas être rétablies de manière récursive.</span><span class="sxs-lookup"><span data-stu-id="6dcb4-102">Custom <xref:System.Text.EncoderFallbackBuffer> instances cannot fall back recursively.</span></span> <span data-ttu-id="6dcb4-103">L’implémentation de <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> doit aboutir à une séquence de caractères convertible en l’encodage de destination.</span><span class="sxs-lookup"><span data-stu-id="6dcb4-103">The implementation of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> must result in a character sequence that is convertible to the destination encoding.</span></span> <span data-ttu-id="6dcb4-104">Dans le cas contraire, une exception se produit.</span><span class="sxs-lookup"><span data-stu-id="6dcb4-104">Otherwise, an exception occurs.</span></span>

#### <a name="change-description"></a><span data-ttu-id="6dcb4-105">Modifier la description</span><span class="sxs-lookup"><span data-stu-id="6dcb4-105">Change description</span></span>

<span data-ttu-id="6dcb4-106">Pendant une opération de transcodage de caractère à octet, le runtime détecte les séquences UTF-16 mal formées ou non convertibles et fournit ces caractères à la méthode <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6dcb4-106">During a character-to-byte transcoding operation, the runtime detects ill-formed or nonconvertible UTF-16 sequences and provides those characters to the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="6dcb4-107">La méthode `Fallback` détermine les caractères qui doivent être substitués aux données d’origine qui ne sont pas convertibles, et ces caractères sont vidés en appelant <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> dans une boucle.</span><span class="sxs-lookup"><span data-stu-id="6dcb4-107">The `Fallback` method determines which characters should be substituted for the original nonconvertible data, and these characters are drained by calling <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> in a loop.</span></span>

<span data-ttu-id="6dcb4-108">Le runtime tente ensuite de transcoder ces caractères de substitution dans l’encodage cible.</span><span class="sxs-lookup"><span data-stu-id="6dcb4-108">The runtime then attempts to transcode these substitution characters to the target encoding.</span></span> <span data-ttu-id="6dcb4-109">Si cette opération a échoué, le runtime continue à effectuer le transcodage à partir de l’endroit où il s’est arrêté dans la chaîne d’entrée d’origine.</span><span class="sxs-lookup"><span data-stu-id="6dcb4-109">If this operation succeeds, the runtime continues transcoding from where it left off in the original input string.</span></span>

<span data-ttu-id="6dcb4-110">Dans .NET Core Preview 7 et les versions antérieures, les implémentations personnalisées de <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> peuvent retourner des séquences de caractères qui ne sont pas convertibles en l’encodage de destination.</span><span class="sxs-lookup"><span data-stu-id="6dcb4-110">In .NET Core Preview 7 and earlier versions, custom implementations of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> can return character sequences that are not convertible to the destination encoding.</span></span> <span data-ttu-id="6dcb4-111">Si les caractères substitués ne peuvent pas être transcodés dans l’encodage cible, le runtime appelle de nouveau la méthode <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> avec les caractères de substitution, en attendant que la méthode <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> retourne une nouvelle séquence de substitution.</span><span class="sxs-lookup"><span data-stu-id="6dcb4-111">If the substituted characters cannot be transcoded to the target encoding, the runtime invokes the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> method once again with the substitution characters, expecting the <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> method to return a new substitution sequence.</span></span> <span data-ttu-id="6dcb4-112">Ce processus se poursuit jusqu’à ce que le Runtime découvre une substitution correctement formée et convertible, ou jusqu’à ce qu’un nombre maximal de récurrences soit atteint.</span><span class="sxs-lookup"><span data-stu-id="6dcb4-112">This process continues until the runtime eventually sees a well-formed, convertible substitution, or until a maximum recursion count is reached.</span></span>

<span data-ttu-id="6dcb4-113">À compter de .NET Core 3,0, les implémentations personnalisées de <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> doivent retourner des séquences de caractères convertibles en encodage de destination.</span><span class="sxs-lookup"><span data-stu-id="6dcb4-113">Starting with .NET Core 3.0, custom implementations of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> must return character sequences that are convertible to the destination encoding.</span></span> <span data-ttu-id="6dcb4-114">Si les caractères substitués ne peuvent pas être transcodés dans l’encodage cible, une <xref:System.ArgumentException> est levée.</span><span class="sxs-lookup"><span data-stu-id="6dcb4-114">If the substituted characters cannot be transcoded to the target encoding, an <xref:System.ArgumentException> is thrown.</span></span> <span data-ttu-id="6dcb4-115">Le runtime n’effectue plus d’appels récursifs dans l’instance <xref:System.Text.EncoderFallbackBuffer>.</span><span class="sxs-lookup"><span data-stu-id="6dcb4-115">The runtime will no longer make recursive calls into the <xref:System.Text.EncoderFallbackBuffer> instance.</span></span>

<span data-ttu-id="6dcb4-116">Ce comportement s’applique uniquement lorsque les trois conditions suivantes sont remplies :</span><span class="sxs-lookup"><span data-stu-id="6dcb4-116">This behavior only applies when all three of the following conditions are met:</span></span>

- <span data-ttu-id="6dcb4-117">Le runtime détecte une séquence UTF-16 ou UTF-16 incorrecte qui ne peut pas être convertie en l’encodage cible.</span><span class="sxs-lookup"><span data-stu-id="6dcb4-117">The runtime detects an ill-formed UTF-16 sequence or a UTF-16 sequence that cannot be converted to the target encoding.</span></span>
- <span data-ttu-id="6dcb4-118">Un <xref:System.Text.EncoderFallback> personnalisé a été spécifié.</span><span class="sxs-lookup"><span data-stu-id="6dcb4-118">A custom <xref:System.Text.EncoderFallback> has been specified.</span></span>
- <span data-ttu-id="6dcb4-119">Le <xref:System.Text.EncoderFallback> personnalisé tente de substituer une nouvelle séquence UTF-16 incorrecte ou non convertible.</span><span class="sxs-lookup"><span data-stu-id="6dcb4-119">The custom <xref:System.Text.EncoderFallback> attempts to substitute a new ill-formed or nonconvertible UTF-16 sequence.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6dcb4-120">Version introduite</span><span class="sxs-lookup"><span data-stu-id="6dcb4-120">Version introduced</span></span>

<span data-ttu-id="6dcb4-121">3.0</span><span class="sxs-lookup"><span data-stu-id="6dcb4-121">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6dcb4-122">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="6dcb4-122">Recommended action</span></span>

<span data-ttu-id="6dcb4-123">La plupart des développeurs n’ont aucune action à effectuer.</span><span class="sxs-lookup"><span data-stu-id="6dcb4-123">Most developers needn't take any action.</span></span>

<span data-ttu-id="6dcb4-124">Si une application utilise une <xref:System.Text.EncoderFallback> personnalisée et <xref:System.Text.EncoderFallbackBuffer> classe, assurez-vous que l’implémentation de <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> remplit la mémoire tampon de secours avec des données UTF-16 bien formées qui sont directement convertibles en l’encodage cible lorsque la méthode <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> est appelée pour la première fois par le Runtime.</span><span class="sxs-lookup"><span data-stu-id="6dcb4-124">If an application uses a custom <xref:System.Text.EncoderFallback> and <xref:System.Text.EncoderFallbackBuffer> class, ensure the implementation of <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> populates the fallback buffer with well-formed UTF-16 data that is directly convertible to the target encoding when the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> method is first invoked by the runtime.</span></span>

#### <a name="category"></a><span data-ttu-id="6dcb4-125">Category</span><span class="sxs-lookup"><span data-stu-id="6dcb4-125">Category</span></span>

<span data-ttu-id="6dcb4-126">CoreFx</span><span class="sxs-lookup"><span data-stu-id="6dcb4-126">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6dcb4-127">API affectées</span><span class="sxs-lookup"><span data-stu-id="6dcb4-127">Affected APIs</span></span>

- <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>
- <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Text.EncoderFallbackBuffer.Fallback`
- `M:System.Text.EncoderFallbackBuffer.GetNextChar`

-->
---
ms.openlocfilehash: 4075eadf7cfb39c913b7657d43335bae5497deff
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71217051"
---
### <a name="custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively"></a><span data-ttu-id="27326-101">Les instances EncoderFallbackBuffer personnalisées ne peuvent pas être rétablies de manière récursive</span><span class="sxs-lookup"><span data-stu-id="27326-101">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>

<span data-ttu-id="27326-102">Les <xref:System.Text.EncoderFallbackBuffer> instances personnalisées ne peuvent pas être rétablies de manière récursive.</span><span class="sxs-lookup"><span data-stu-id="27326-102">Custom <xref:System.Text.EncoderFallbackBuffer> instances cannot fall back recursively.</span></span> <span data-ttu-id="27326-103">L’implémentation de <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> doit entraîner une séquence de caractères convertible en l’encodage de destination.</span><span class="sxs-lookup"><span data-stu-id="27326-103">The implementation of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> must result in a character sequence that is convertible to the destination encoding.</span></span> <span data-ttu-id="27326-104">Dans le cas contraire, une exception se produit.</span><span class="sxs-lookup"><span data-stu-id="27326-104">Otherwise, an exception occurs.</span></span>

#### <a name="details"></a><span data-ttu-id="27326-105">Détails</span><span class="sxs-lookup"><span data-stu-id="27326-105">Details</span></span>

<span data-ttu-id="27326-106">Pendant une opération de transcodage de caractère à octet, le runtime détecte les séquences UTF-16 mal formées ou non convertibles et fournit ces caractères à <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> la méthode.</span><span class="sxs-lookup"><span data-stu-id="27326-106">During a character-to-byte transcoding operation, the runtime detects ill-formed or nonconvertible UTF-16 sequences and provides those characters to the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="27326-107">La `Fallback` méthode détermine les caractères qui doivent être substitués aux données d’origine qui ne sont pas convertibles, et ces caractères <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> sont vidés en appelant dans une boucle.</span><span class="sxs-lookup"><span data-stu-id="27326-107">The `Fallback` method determines which characters should be substituted for the original nonconvertible data, and these characters are drained by calling <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> in a loop.</span></span>

<span data-ttu-id="27326-108">Le runtime tente ensuite de transcoder ces caractères de substitution dans l’encodage cible.</span><span class="sxs-lookup"><span data-stu-id="27326-108">The runtime then attempts to transcode these substitution characters to the target encoding.</span></span> <span data-ttu-id="27326-109">Si cette opération a échoué, le runtime continue à effectuer le transcodage à partir de l’endroit où il s’est arrêté dans la chaîne d’entrée d’origine.</span><span class="sxs-lookup"><span data-stu-id="27326-109">If this operation succeeds, the runtime continues transcoding from where it left off in the original input string.</span></span>

<span data-ttu-id="27326-110">Dans .net Core Preview 7 et les versions antérieures, les implémentations <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> personnalisées de peuvent retourner des séquences de caractères qui ne sont pas convertibles en l’encodage de destination.</span><span class="sxs-lookup"><span data-stu-id="27326-110">In .NET Core Preview 7 and earlier versions, custom implementations of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> can return character sequences that are not convertible to the destination encoding.</span></span> <span data-ttu-id="27326-111">Si les caractères substitués ne peuvent pas être transcodés en l’encodage cible, le runtime <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> appelle de nouveau la méthode avec les caractères de substitution, <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> en attendant que la méthode retourne une nouvelle séquence de substitution.</span><span class="sxs-lookup"><span data-stu-id="27326-111">If the substituted characters cannot be transcoded to the target encoding, the runtime invokes the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> method once again with the substitution characters, expecting the <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> method to return a new substitution sequence.</span></span> <span data-ttu-id="27326-112">Ce processus se poursuit jusqu’à ce que le Runtime découvre une substitution correctement formée et convertible, ou jusqu’à ce qu’un nombre maximal de récurrences soit atteint.</span><span class="sxs-lookup"><span data-stu-id="27326-112">This process continues until the runtime eventually sees a well-formed, convertible substitution, or until a maximum recursion count is reached.</span></span>

<span data-ttu-id="27326-113">À compter de .net Core 3,0, les implémentations <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> personnalisées de doivent retourner des séquences de caractères convertibles en l’encodage de destination.</span><span class="sxs-lookup"><span data-stu-id="27326-113">Starting with .NET Core 3.0, custom implementations of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> must return character sequences that are convertible to the destination encoding.</span></span> <span data-ttu-id="27326-114">Si les caractères substitués ne peuvent pas être transcodés en l’encodage <xref:System.ArgumentException> cible, une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="27326-114">If the substituted characters cannot be transcoded to the target encoding, an <xref:System.ArgumentException> is thrown.</span></span> <span data-ttu-id="27326-115">Le runtime n’effectue plus d’appels récursifs dans l' <xref:System.Text.EncoderFallbackBuffer> instance.</span><span class="sxs-lookup"><span data-stu-id="27326-115">The runtime will no longer make recursive calls into the <xref:System.Text.EncoderFallbackBuffer> instance.</span></span>

<span data-ttu-id="27326-116">Ce comportement s’applique uniquement lorsque les trois conditions suivantes sont remplies :</span><span class="sxs-lookup"><span data-stu-id="27326-116">This behavior only applies when all three of the following conditions are met:</span></span>

- <span data-ttu-id="27326-117">Le runtime détecte une séquence UTF-16 ou UTF-16 incorrecte qui ne peut pas être convertie en l’encodage cible.</span><span class="sxs-lookup"><span data-stu-id="27326-117">The runtime detects an ill-formed UTF-16 sequence or a UTF-16 sequence that cannot be converted to the target encoding.</span></span>
- <span data-ttu-id="27326-118">Un personnalisé <xref:System.Text.EncoderFallback> a été spécifié.</span><span class="sxs-lookup"><span data-stu-id="27326-118">A custom <xref:System.Text.EncoderFallback> has been specified.</span></span>
- <span data-ttu-id="27326-119">Le personnalisé <xref:System.Text.EncoderFallback> tente de substituer une nouvelle séquence UTF-16 incorrecte ou non convertible.</span><span class="sxs-lookup"><span data-stu-id="27326-119">The custom <xref:System.Text.EncoderFallback> attempts to substitute a new ill-formed or nonconvertible UTF-16 sequence.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="27326-120">Version introduite</span><span class="sxs-lookup"><span data-stu-id="27326-120">Version introduced</span></span>

<span data-ttu-id="27326-121">3.0</span><span class="sxs-lookup"><span data-stu-id="27326-121">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="27326-122">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="27326-122">Recommended action</span></span>

<span data-ttu-id="27326-123">La plupart des développeurs n’ont aucune action à effectuer.</span><span class="sxs-lookup"><span data-stu-id="27326-123">Most developers needn't take any action.</span></span>

<span data-ttu-id="27326-124">Si une application utilise une classe <xref:System.Text.EncoderFallback> et <xref:System.Text.EncoderFallbackBuffer> personnalisée, assurez-vous <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> que l’implémentation de remplit la mémoire tampon de secours avec des données UTF-16 bien formées qui sont directement convertibles en l’encodage cible lorsque la <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> méthode est d’abord appelé par le Runtime.</span><span class="sxs-lookup"><span data-stu-id="27326-124">If an application uses a custom <xref:System.Text.EncoderFallback> and <xref:System.Text.EncoderFallbackBuffer> class, ensure the implementation of <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> populates the fallback buffer with well-formed UTF-16 data that is directly convertible to the target encoding when the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> method is first invoked by the runtime.</span></span>

#### <a name="category"></a><span data-ttu-id="27326-125">Category</span><span class="sxs-lookup"><span data-stu-id="27326-125">Category</span></span>

<span data-ttu-id="27326-126">CoreFx</span><span class="sxs-lookup"><span data-stu-id="27326-126">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="27326-127">API affectées</span><span class="sxs-lookup"><span data-stu-id="27326-127">Affected APIs</span></span>

- <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>
- <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Text.EncoderFallbackBuffer.Fallback`
- `M:System.Text.EncoderFallbackBuffer.GetNextChar`

-->

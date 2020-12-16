---
title: AVERTISSEMENT SYSLIB0001
description: En savoir plus sur les obsoletions qui génèrent un avertissement au moment de la compilation SYSLIB0001.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 6c4b6a2f41e9dc044ef76bb5a53a4a54a44bca5a
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/16/2020
ms.locfileid: "97596535"
---
# <a name="syslib0001-the-utf-7-encoding-is-insecure"></a><span data-ttu-id="3e9e1-103">SYSLIB0001 : l’encodage UTF-7 n’est pas sécurisé</span><span class="sxs-lookup"><span data-stu-id="3e9e1-103">SYSLIB0001: The UTF-7 encoding is insecure</span></span>

<span data-ttu-id="3e9e1-104">L’encodage UTF-7 n’est plus utilisé dans les applications, et de nombreuses spécifications [interdisent désormais son utilisation](https://security.stackexchange.com/a/68609/3573) dans l’échange.</span><span class="sxs-lookup"><span data-stu-id="3e9e1-104">The UTF-7 encoding is no longer in wide use among applications, and many specs now [forbid its use](https://security.stackexchange.com/a/68609/3573) in interchange.</span></span> <span data-ttu-id="3e9e1-105">Il est également occasionnellement [utilisé comme vecteur d’attaque dans les](https://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=utf-7) applications qui ne prévoient pas la présence de données encodées en UTF-7.</span><span class="sxs-lookup"><span data-stu-id="3e9e1-105">It's also occasionally [used as an attack vector](https://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=utf-7) in applications that don't anticipate encountering UTF-7-encoded data.</span></span> <span data-ttu-id="3e9e1-106">Microsoft vous avertit de l’utilisation de <xref:System.Text.UTF7Encoding?displayProperty=nameWithType> car il ne fournit pas de détection d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="3e9e1-106">Microsoft warns against use of <xref:System.Text.UTF7Encoding?displayProperty=nameWithType> because it doesn't provide error detection.</span></span>

<span data-ttu-id="3e9e1-107">Par conséquent, les API suivantes sont marquées comme obsolètes, à partir de .NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="3e9e1-107">Consequently, the following APIs are marked obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="3e9e1-108">L’utilisation de ces API génère un avertissement `SYSLIB0001` au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="3e9e1-108">Use of these APIs generates warning `SYSLIB0001` at compile time.</span></span>

- <span data-ttu-id="3e9e1-109">Propriété<xref:System.Text.Encoding.UTF7?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="3e9e1-109"><xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> property</span></span>
- <span data-ttu-id="3e9e1-110"><xref:System.Text.UTF7Encoding.%23ctor%2A> constructeurs</span><span class="sxs-lookup"><span data-stu-id="3e9e1-110"><xref:System.Text.UTF7Encoding.%23ctor%2A> constructors</span></span>

## <a name="workarounds"></a><span data-ttu-id="3e9e1-111">Solutions de contournement</span><span class="sxs-lookup"><span data-stu-id="3e9e1-111">Workarounds</span></span>

- <span data-ttu-id="3e9e1-112">Si vous utilisez <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> ou <xref:System.Text.UTF7Encoding> dans votre propre protocole ou format de fichier :</span><span class="sxs-lookup"><span data-stu-id="3e9e1-112">If you're using <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> or <xref:System.Text.UTF7Encoding> within your own protocol or file format:</span></span>

  <span data-ttu-id="3e9e1-113">Basculez vers à l’aide de <xref:System.Text.Encoding.UTF8?displayProperty=nameWithType> ou <xref:System.Text.UTF8Encoding> .</span><span class="sxs-lookup"><span data-stu-id="3e9e1-113">Switch to using <xref:System.Text.Encoding.UTF8?displayProperty=nameWithType> or <xref:System.Text.UTF8Encoding>.</span></span> <span data-ttu-id="3e9e1-114">UTF-8 est une norme de l’industrie qui est largement prise en charge dans les langages, les systèmes d’exploitation et les runtimes.</span><span class="sxs-lookup"><span data-stu-id="3e9e1-114">UTF-8 is an industry standard and is widely supported across languages, operating systems, and runtimes.</span></span> <span data-ttu-id="3e9e1-115">L’utilisation d’UTF-8 facilite la maintenance à venir de votre code et le rend plus interopérable avec le reste de l’écosystème.</span><span class="sxs-lookup"><span data-stu-id="3e9e1-115">Using UTF-8 eases future maintenance of your code and makes it more interoperable with the rest of the ecosystem.</span></span>

- <span data-ttu-id="3e9e1-116">Si vous comparez une <xref:System.Text.Encoding> instance à <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="3e9e1-116">If you're comparing an <xref:System.Text.Encoding> instance against <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType>:</span></span>

  <span data-ttu-id="3e9e1-117">Au lieu de cela, envisagez d’effectuer une vérification par rapport à la page de codes UTF-7 connue, qui est `65000` .</span><span class="sxs-lookup"><span data-stu-id="3e9e1-117">Instead, consider performing a check against the well-known UTF-7 code page, which is `65000`.</span></span> <span data-ttu-id="3e9e1-118">En comparant à la page de codes, vous évitez l’avertissement et vous gérez également certains cas limites, par exemple si quelqu’un a appelé ou sous- `new UTF7Encoding()` classé le type.</span><span class="sxs-lookup"><span data-stu-id="3e9e1-118">By comparing against the code page, you avoid the warning and also handle some edge cases, such as if somebody called `new UTF7Encoding()` or subclassed the type.</span></span>

  ```csharp
  void DoSomething(Encoding enc)
  {
      // Don't perform the check this way.
      // It produces a warning and misses some edge cases.
      if (enc == Encoding.UTF7)
      {
          // Encoding is UTF-7.
      }

      // Instead, perform the check this way.
      if (enc != null && enc.CodePage == 65000)
      {
          // Encoding is UTF-7.
      }
  }
  ```

[!INCLUDE [suppress-syslib-warning](../../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a><span data-ttu-id="3e9e1-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3e9e1-119">See also</span></span>

- [<span data-ttu-id="3e9e1-120">Les chemins d’accès en code UTF-7 sont obsolètes</span><span class="sxs-lookup"><span data-stu-id="3e9e1-120">UTF-7 code paths are obsolete</span></span>](../core-libraries/5.0/utf-7-code-paths-obsolete.md)

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
# <a name="syslib0001-the-utf-7-encoding-is-insecure"></a>SYSLIB0001 : l’encodage UTF-7 n’est pas sécurisé

L’encodage UTF-7 n’est plus utilisé dans les applications, et de nombreuses spécifications [interdisent désormais son utilisation](https://security.stackexchange.com/a/68609/3573) dans l’échange. Il est également occasionnellement [utilisé comme vecteur d’attaque dans les](https://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=utf-7) applications qui ne prévoient pas la présence de données encodées en UTF-7. Microsoft vous avertit de l’utilisation de <xref:System.Text.UTF7Encoding?displayProperty=nameWithType> car il ne fournit pas de détection d’erreurs.

Par conséquent, les API suivantes sont marquées comme obsolètes, à partir de .NET 5,0. L’utilisation de ces API génère un avertissement `SYSLIB0001` au moment de la compilation.

- Propriété<xref:System.Text.Encoding.UTF7?displayProperty=nameWithType>
- <xref:System.Text.UTF7Encoding.%23ctor%2A> constructeurs

## <a name="workarounds"></a>Solutions de contournement

- Si vous utilisez <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> ou <xref:System.Text.UTF7Encoding> dans votre propre protocole ou format de fichier :

  Basculez vers à l’aide de <xref:System.Text.Encoding.UTF8?displayProperty=nameWithType> ou <xref:System.Text.UTF8Encoding> . UTF-8 est une norme de l’industrie qui est largement prise en charge dans les langages, les systèmes d’exploitation et les runtimes. L’utilisation d’UTF-8 facilite la maintenance à venir de votre code et le rend plus interopérable avec le reste de l’écosystème.

- Si vous comparez une <xref:System.Text.Encoding> instance à <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> :

  Au lieu de cela, envisagez d’effectuer une vérification par rapport à la page de codes UTF-7 connue, qui est `65000` . En comparant à la page de codes, vous évitez l’avertissement et vous gérez également certains cas limites, par exemple si quelqu’un a appelé ou sous- `new UTF7Encoding()` classé le type.

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

## <a name="see-also"></a>Voir aussi

- [Les chemins d’accès en code UTF-7 sont obsolètes](../core-libraries/5.0/utf-7-code-paths-obsolete.md)

---
title: Délimiteurs pour les balises de documentation-Guide de programmation C#
description: En savoir plus sur les délimiteurs pour les balises de documentation. Les délimiteurs indiquent au compilateur où un commentaire de documentation commence et se termine.
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], delimiters
- /** */ delimiters for C# documentation tags
- /// delimiter for C# documentation
ms.assetid: 9b2bdd18-4f5c-4c0b-988e-fb992e0d233e
ms.openlocfilehash: 3191e32b0ff2dbde004abaab0b699cd61fcbb150
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381981"
---
# <a name="delimiters-for-documentation-tags-c-programming-guide"></a>Délimiteurs pour les balises de documentation (Guide de programmation C#)

L’utilisation de commentaires de documentation XML exige des délimiteurs, qui indiquent au compilateur où un commentaire de documentation commence et se termine. Vous pouvez utiliser les genres de délimiteurs ci-dessous avec les balises de documentation XML :

- `///`

  Délimiteur à une ligne. Il s’agit de la forme qui est présentée dans les exemples de documentation et utilisée par les modèles de projet C#. Si un caractère espace blanc suit le délimiteur, ce caractère n’est pas inclus dans la sortie XML.

  > [!NOTE]
  > L’environnement de développement intégré (IDE) de Visual Studio insère automatiquement `<summary>` les `</summary>` balises et et déplace le curseur dans ces balises après que vous avez tapé le `///` délimiteur dans l’éditeur de code. Vous pouvez activer/désactiver cette fonctionnalité dans la [boîte de dialogue Options](/visualstudio/ide/reference/options-text-editor-csharp-advanced).
  
- `/** */`

  Séparateurs multilignes.

  Certaines règles de mise en forme doivent être respectées lorsque vous utilisez les `/** */` délimiteurs :
  
  - Sur la ligne qui contient le délimiteur `/**`, si le reste de la ligne n’est constitué que d’espace blanc, la ligne n’est pas traitée pour les commentaires. Si le premier caractère après le délimiteur `/**` est un espace blanc, celui-ci est ignoré et le reste de la ligne est traité. Sinon, tout le texte de la ligne après le délimiteur `/**` est traité comme faisant partie du commentaire.

  - Sur la ligne qui contient le délimiteur `*/`, s’il n’y a que des espaces blancs jusqu’au délimiteur `*/`, cette ligne est ignorée. Dans le cas contraire, le texte sur la ligne jusqu’au `*/` délimiteur est traité dans le cadre du commentaire.
  
  - Pour les lignes situées après celle qui commence par le délimiteur `/**`, le compilateur recherche un modèle commun au début de chaque ligne. Le modèle peut se composer d’un espace blanc facultatif et d’un astérisque (`*`), suivi d’autres espaces blancs facultatifs. Si le compilateur détecte un modèle commun au début de chaque ligne qui ne commence pas par le délimiteur `/**` ou `*/`, il ignore ce modèle pour chaque ligne.

  Les exemples suivants illustrent ces règles.

  - La seule partie du commentaire suivant traitée est la ligne qui commence par `<summary>` . Les trois formats de balise produisent les mêmes commentaires.

    ```csharp
    /** <summary>text</summary> */

    /**
    <summary>text</summary>
    */

    /**
     * <summary>text</summary>
    */
    ```

  - Le compilateur identifie un modèle commun de « \* » au début des deuxième et troisième lignes. Le modèle n’est pas inclus dans la sortie.

    ```csharp
    /**
     * <summary>
     * text </summary>*/
    ```

  - Le compilateur ne détecte aucun modèle commun dans le commentaire suivant, car le deuxième caractère sur la troisième ligne n’est pas un astérisque. Ainsi, tout le texte des deuxième et troisième lignes est traité comme faisant partie du commentaire.

    ```csharp
    /**
     * <summary>
       text </summary>
    */
    ```

  - Le compilateur ne détecte aucun modèle dans le commentaire suivant pour deux raisons. Tout d’abord, le nombre d’espaces avant l’astérisque n’est pas cohérent. Ensuite, la cinquième ligne commence par une tabulation, qui ne correspond pas à des espaces. Ainsi, tout le texte des lignes deux à cinq est traité comme faisant partie du commentaire.

    <!-- markdownlint-disable MD010 -->
    ```csharp
    /**
      * <summary>
      * text
     *  text2
        *  </summary>
    */
    ```
    <!-- markdownlint-enable MD010 -->

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Commentaires sur la documentation XML](./index.md)
- [-doc (options du compilateur C#)](../../language-reference/compiler-options/doc-compiler-option.md)

---
title: Guide pratique pour utiliser les fonctionnalités de la documentation XML-Guide de programmation C#
description: Découvrez comment utiliser les fonctionnalités de la documentation XML. Consultez des exemples de code et affichez des ressources disponibles supplémentaires.
ms.date: 06/01/2018
helpviewer_keywords:
- XML documentation [C#]
- C# language, XML documentation features
ms.assetid: 8f33917b-9577-4c9a-818a-640dbbb0b399
ms.openlocfilehash: 9ad2cfe62c70174eec9020ad4c8ce11608aca36d
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87380668"
---
# <a name="how-to-use-the-xml-documentation-features"></a>Comment utiliser les fonctionnalités de la documentation XML

L’exemple suivant montre un type qui a été documenté.

## <a name="example"></a>Exemple

[!code-csharp[csProgGuideDocComments#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#15)]

L’exemple génère un fichier *. xml* avec le contenu suivant.

```xml
<?xml version="1.0"?>
<doc>
    <assembly>
        <name>xmlsample</name>
    </assembly>
    <members>
        <member name="T:TestClass">
            <summary>
            Class level summary documentation goes here.
            </summary>
            <remarks>
            Longer comments can be associated with a type or member through
            the remarks tag.
            </remarks>
        </member>
        <member name="F:TestClass._name">
            <summary>
            Store for the Name property.
            </summary>
        </member>
        <member name="M:TestClass.#ctor">
            <summary>
            The class constructor.
            </summary>
        </member>
        <member name="P:TestClass.Name">
            <summary>
            Name property.
            </summary>
            <value>
            A value tag is used to describe the property value.
            </value>
        </member>
        <member name="M:TestClass.SomeMethod(System.String)">
            <summary>
            Description for SomeMethod.
            </summary>
            <param name="s"> Parameter description for s goes here.</param>
            <seealso cref="T:System.String">
            You can use the cref attribute on any tag to reference a type or member
            and the compiler will check that the reference exists.
            </seealso>
        </member>
        <member name="M:TestClass.SomeOtherMethod">
            <summary>
            Some other method.
            </summary>
            <returns>
            Return values are described through the returns tag.
            </returns>
            <seealso cref="M:TestClass.SomeMethod(System.String)">
            Notice the use of the cref attribute to reference a specific method.
            </seealso>
        </member>
        <member name="M:TestClass.Main(System.String[])">
            <summary>
            The entry point for the application.
            </summary>
            <param name="args"> A list of command line arguments.</param>
        </member>
        <member name="T:TestInterface">
            <summary>
            Documentation that describes the interface goes here.
            </summary>
            <remarks>
            Details about the interface go here.
            </remarks>
        </member>
        <member name="M:TestInterface.InterfaceMethod(System.Int32)">
            <summary>
            Documentation that describes the method goes here.
            </summary>
            <param name="n">
            Parameter n requires an integer argument.
            </param>
            <returns>
            The method returns an integer.
            </returns>
        </member>
    </members>
</doc>
```

## <a name="compiling-the-code"></a>Compilation du code

Pour compiler l’exemple, entrez la commande suivante :

`csc XMLsample.cs /doc:XMLsample.xml`

Cette commande crée le fichier XML *XMLsample.xml*, que vous pouvez afficher dans votre navigateur ou à l’aide de la `TYPE` commande.

## <a name="robust-programming"></a>Programmation fiable

La documentation XML commence par `///` . Lorsque vous créez un projet, les assistants placent des lignes de démarrage `///` pour vous. Le traitement de ces commentaires présente certaines restrictions :

- La documentation doit être dans un format XML correct. Si le XML n’est pas correct, un avertissement est généré. En outre, un commentaire indiquant qu’une erreur s’est produite est ajouté au fichier de documentation.

- Les développeurs sont libres de créer leur propre jeu de balises. Il existe un [ensemble recommandé de balises](recommended-tags-for-documentation-comments.md). Certaines des balises recommandées ont des significations spéciales :

  - La `<param>` balise est utilisée pour décrire les paramètres. Quand elle est utilisée, le compilateur vérifie que le paramètre existe et que tous les paramètres sont décrits dans la documentation. Si la vérification échoue, le compilateur émet un avertissement.

  - L' `cref` attribut peut être attaché à n’importe quelle balise pour référencer un élément de code. Le compilateur vérifie l’existence de cet élément de code. Si la vérification échoue, le compilateur émet un avertissement. Le compilateur respecte toutes les instructions `using` lorsqu’il recherche un type décrit dans l’attribut `cref`.

  - La `<summary>` balise est utilisée par IntelliSense dans Visual Studio pour afficher des informations supplémentaires sur un type ou un membre.

    > [!NOTE]
    > Le fichier XML ne fournit pas des informations complètes sur le type et les membres (par exemple, il ne contient pas d’informations sur le type). Pour obtenir des informations complètes sur un type ou un membre, utilisez le fichier de documentation ainsi que la réflexion sur le type ou le membre réel.

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [-doc (options du compilateur C#)](../../language-reference/compiler-options/doc-compiler-option.md)
- [Commentaires sur la documentation XML](./index.md)
- [Processeur de documentation DocFX](https://dotnet.github.io/docfx/)
- [Processeur de documentation Sandcastle](https://github.com/EWSoftware/SHFB)

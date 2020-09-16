---
title: Considérations relatives à la version et la mise à jour pour les développeurs C#
description: L’introduction de nouvelles fonctionnalités de langage dans votre bibliothèque peut affecter le code qui l’utilise.
ms.topic: reference
ms.date: 09/19/2018
ms.openlocfilehash: 6de0e3ba33af34edba73819dcb9268f40f8a5ea4
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90552425"
---
# <a name="version-and-update-considerations-for-c-developers"></a>Considérations relatives à la version et la mise à jour pour les développeurs C#

La compatibilité est un objectif très important alors que des nouvelles fonctionnalités sont ajoutées au langage C#. Dans presque tous les cas, le code existant peut être recompilé avec une nouvelle version du compilateur sans problème.

Vous devrez peut-être faire plus attention lorsque vous adoptez de nouvelles fonctionnalités de langage dans une bibliothèque. Vous créez peut-être une nouvelle bibliothèque avec des fonctionnalités incluses dans la version la plus récente et avez besoin de vous assurer que les applications créées à l’aide de versions précédentes du compilateur peuvent l’utiliser. Ou vous mettez peut-être à niveau une bibliothèque existante et la plupart de vos utilisateurs ne disposent pas encore des versions mises à niveau. Lorsque vous prenez des décisions sur l’adoption de nouvelles fonctionnalités, vous devez prendre en compte deux variantes de la compatibilité : compatibilité avec la source et compatibilité binaire.

## <a name="binary-compatible-changes"></a>Modifications compatibles binaires

Les modifications apportées à votre bibliothèque sont **compatibles binaires** lorsque votre bibliothèque mise à jour peut être utilisée sans régénération des applications et des bibliothèques qui l’utilisent. Les assemblys dépendants n’ont pas besoin d’être reconstruits et aucune modification du code source n’est requise. Les modifications compatibles binaires sont également des modifications compatibles avec la source.

## <a name="source-compatible-changes"></a>Modifications compatibles avec la source

Les modifications apportées à votre bibliothèque sont **compatibles avec la source** lorsque les applications et les bibliothèques qui utilisent votre bibliothèque ne nécessitent pas de modifications du code source, mais que la source doit être recompilée avec la nouvelle version pour fonctionner correctement.

## <a name="incompatible-changes"></a>Modifications incompatibles

Si une modification n’est ni **compatible avec la source** ni **compatible binaire**, des modifications du code source, ainsi qu’une recompilation sont requises dans les applications et les bibliothèques dépendantes.

## <a name="evaluate-your-library"></a>Évaluer votre bibliothèque

Ces concepts de compatibilité affectent les déclarations publiques et protégées de votre bibliothèque, pas son implémentation interne. L’adoption de nouvelles fonctionnalités en interne est toujours **compatible binaire**.  

Les modifications **compatibles binaires** fournissent une nouvelle syntaxe qui génère le même code compilé pour les déclarations publiques que l’ancienne syntaxe. Par exemple, la modification d’une méthode en un membre expression-bodied est une modification **compatible binaire** :

Code d'origine :

```csharp
public double CalculateSquare(double value)
{
    return value * value;
}
```

Nouveau code :

```csharp
public double CalculateSquare(double value) => value * value;
```

Les modifications **compatibles avec la source** introduisent une syntaxe qui modifie le code compilé pour un membre public, mais de manière compatible avec les sites d’appel existants. Par exemple, la modification d’une signature de méthode à partir d’un paramètre de valeur by en un paramètre de référence by `in` est compatible avec la source mais pas compatible binaire :

Code d'origine :

```csharp
public double CalculateSquare(double value) => value * value;
```

Nouveau code :

```csharp
public double CalculateSquare(in double value) => value * value;
```

Les articles [Nouveautés](./csharp-9.md) indiquent si l’introduction d’une fonctionnalité qui affecte les déclarations publiques est compatible avec la source ou compatible binaire.

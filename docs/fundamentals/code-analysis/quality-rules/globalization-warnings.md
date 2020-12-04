---
title: Règles de globalisation (analyse du code)
description: En savoir plus sur les règles de globalisation des règles d’analyse du code
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.globalizationrules
helpviewer_keywords:
- rules, globalization
- globalization rules
- globalization [Visual Studio], rules
- managed code analysis rules, globalization rules
author: gewarren
ms.author: gewarren
ms.openlocfilehash: 83ecc52c5e20e074c6c1aed68204a574494f42d5
ms.sourcegitcommit: 2e4adc490c1d2a705a0592b295d606b10b9f51f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2020
ms.locfileid: "96587621"
---
# <a name="globalization-rules"></a>Règles de globalisation

Les règles de globalisation prennent en charge des bibliothèques et des applications mondialisables.

## <a name="in-this-section"></a>Dans cette section

|Règle|Description|
|----------|-----------------|
|[CA1303 : Ne pas passer de littéraux en paramètres localisés](ca1303.md)|Une méthode visible de l’extérieur passe un littéral de chaîne en tant que paramètre à une méthode ou un constructeur .NET, et cette chaîne doit être localisable.|
|[CA1304 : Spécifier CultureInfo](ca1304.md)|Une méthode ou un constructeur appelle un membre présentant une surcharge qui accepte un paramètre System.Globalization.CultureInfo, et la méthode ou le constructeur n'appelle pas la surcharge qui prend le paramètre CultureInfo. Lorsqu'un objet CultureInfo ou System.IFormatProvider n'est pas fourni, la valeur par défaut fournie par le membre surchargé peut ne pas avoir l'effet escompté selon les différents paramètres régionaux.|
|[CA1305 : Spécifier IFormatProvider](ca1305.md)|Une méthode ou un constructeur appelle un ou plusieurs membres présentant des surcharges qui acceptent un paramètre System.IFormatProvider, et la méthode ou le constructeur n'appelle pas la surcharge qui prend le paramètre IFormatProvider. Lorsqu'un objet System.Globalization.CultureInfo ou IFormatProvider n'est pas fourni, la valeur par défaut fournie par le membre surchargé peut ne pas avoir l'effet escompté selon les différents paramètres régionaux.|
|[CA1307 : Spécifier StringComparison pour clarifier](ca1307.md)|Une opération de comparaison de chaînes utilise une surcharge de méthode qui ne définit pas de paramètre StringComparison.|
|[CA1308 : Normaliser les chaînes en majuscules](ca1308.md)|Les chaînes doivent être normalisées en majuscules. En cas de conversion en minuscules, un petit groupe de caractères ne peut pas faire un aller-retour.|
|[CA1309 : Utiliser StringComparison avec la valeur Ordinal](ca1309.md)|Opération de comparaison de chaînes non linguistique qui n'affecte pas la valeur Ordinal ou OrdinalIgnoreCase au paramètre StringComparison. En affectant explicitement au paramètre la valeur StringComparison.Ordinal ou StringComparison.OrdinalIgnoreCase, votre code gagne souvent en rapidité, tout en devenant plus correct et plus fiable.|
|[CA1310 : Spécifier StringComparison pour corriger](ca1310.md)|Une opération de comparaison de chaînes utilise une surcharge de méthode qui ne définit pas de paramètre StringComparison et utilise par défaut la comparaison de chaînes propre à la culture.|
|[CA2101 : spécifiez le marshaling pour les arguments de chaîne P/Invoke](ca2101.md)|Un membre d’appel de code non managé autorise les appelants de confiance partielle, a un paramètre de chaîne et ne marshale pas explicitement la chaîne. Cela peut provoquer une faille de sécurité potentielle.|

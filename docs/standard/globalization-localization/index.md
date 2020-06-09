---
title: Internationalisation et localisation d’applications .NET
description: Découvrez comment développer une application mondialisable. En savoir plus sur la globalisation, la révision d’adaptabilité et la localisation dans .NET.
ms.date: 06/08/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- international applications [.NET]
- globalization [.NET], encoding
- global applications
- internationalization
- world-ready applications
- application development [.NET], globalization
- multilingual application development
ms.assetid: 9a59696b-d89b-45bd-946d-c75da4732d02
ms.openlocfilehash: a3894b7bf9b8aa013b346c169d21c6db270fe987
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600787"
---
# <a name="globalizing-and-localizing-net-applications"></a>Internationalisation et localisation d’applications .NET

Le développement d’une application mondialisable, notamment une application qui peut être localisée dans une ou plusieurs langues, implique trois étapes : la mondialisation, l’étude de la localisabilité et la localisation.

[Globalisation](globalization.md)

Cette étape implique la conception et le codage d'une application indépendante des cultures et des langues qui prend en charge les interfaces utilisateur localisées et les paramètres régionaux pour tous les utilisateurs. Elle implique également de prendre des décisions relatives à la conception et à la programmation qui ne sont pas basées sur des hypothèses spécifiques à la culture. Même si une application globalisée n'est pas localisée, elle est néanmoins conçue et écrite pour pouvoir être ensuite localisée assez facilement en une ou plusieurs langues.

[Révision de l’adaptabilité](localizability-review.md)

Cette étape implique d’examiner le code et la conception d’une application pour vérifier qu’elle peut être localisée facilement et identifier les obstacles éventuels à la localisation, et de vérifier que le code exécutable de l’application est bien séparé de ses ressources. Si la phase de globalisation s'est déroulée correctement, l'examen de la faisabilité de localisation confirmera les choix de conception et de codage effectués pendant la globalisation. La phase d'examen de la faisabilité de localisation peut également identifier les problèmes restants afin de ne pas avoir à modifier le code source d'une application pendant la phase de localisation.

[Localisation](localization.md)

Cette étape implique la personnalisation d'une application pour des cultures ou des régions spécifiques. Si les étapes de globalisation et de faisabilité de localisation ont été effectuées correctement, la localisation consiste principalement à traduire l'interface utilisateur.

L'exécution de ces trois étapes offre deux avantages :

- Vous n'avez plus à adapter a posteriori une application conçue pour prendre en charge une seule culture, telle que l'anglais (États-Unis), pour prendre en charge d'autres cultures.

- Il en résulte des applications localisées plus stables qui présentent moins de bogues.

.NET assure une prise en charge complète du développement d’applications internationalisables et localisées. En particulier, plusieurs membres de type de la bibliothèque de classes .NET facilitent l’internationalisation en retournant des valeurs qui reflètent les conventions de la culture de l’utilisateur actuel ou d’une culture spécifiée. De plus, .NET prend en charge les assemblys satellites, qui simplifient le processus de localisation d’une application.

Pour plus d'informations, consultez la [documentation sur la globalisation](/globalization/).

## <a name="in-this-section"></a>Dans cette section

[Globalisation](globalization.md)

Décrit la première phase de création d'une application mondialisable, qui implique la conception et le codage d'une application indépendante des cultures et des langues.

[Globalisation et ICU .NET](globalization-icu.md)

Décrit comment la globalisation .NET utilise [les composants internationaux pour Unicode (ICU)](http://site.icu-project.org/home).

[Révision de l’adaptabilité](localizability-review.md)

Décrit la seconde phase de création d'une application localisée, qui implique l'identification d'obstacles éventuels à la localisation.

[Localisation](localization.md)

Décrit la phase finale de la création d'une application localisée, qui implique la personnalisation de l'interface utilisateur d'une application en fonction de régions ou de cultures spécifiques.

[Opérations de chaînes indépendantes de la culture](culture-insensitive-string-operations.md)

Explique comment utiliser les méthodes et les classes .NET dépendantes de la culture par défaut pour obtenir des résultats indépendants de la culture.

[Bonnes pratiques pour développer des applications internationales](best-practices-for-developing-world-ready-apps.md)

Décrit les meilleures pratiques en matière de globalisation, de localisation et de développement d'applications ASP.NET mondialisables.

## <a name="reference"></a>Informations de référence

- Espace de noms <xref:System.Globalization?displayProperty=nameWithType>

   Contient des classes qui définissent des informations liées à la culture, notamment la langue, le pays ou la région, les calendriers utilisés, les formats des dates, des monnaies et des nombres, ainsi que l'ordre de tri à respecter pour les chaînes.

- Espace de noms <xref:System.Resources>

   Fournit des classes pour créer, manipuler et utiliser des ressources.

- Espace de noms <xref:System.Text>

   Contient des classes représentant les encodages de caractères ASCII, ANSI, Unicode et autres.

- [Resgen. exe (générateur de fichier de ressources)](../../framework/tools/resgen-exe-resource-file-generator.md)

   Explique comment utiliser Resgen.exe pour convertir des fichiers .txt et des fichiers .resx (format de ressource basé sur XML) en fichiers binaires .resources du Common Language Runtime.

- [Winres. exe (Windows Forms éditeur de ressources)](../../framework/tools/winres-exe-windows-forms-resource-editor.md)

   Explique comment utiliser Winres.exe pour localiser des formulaires Windows Forms.

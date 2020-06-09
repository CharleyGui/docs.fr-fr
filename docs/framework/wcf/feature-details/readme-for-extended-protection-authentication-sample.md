---
title: ReadMe pour l'exemple d'authentification de protection étendue
ms.date: 03/30/2017
ms.assetid: 80bf2e97-398d-4db5-9040-d96478a2ccab
ms.openlocfilehash: 9b0a3535282a1fcc1103651f5601459e80d3d8d4
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601099"
---
# <a name="readme-for-extended-protection-authentication-sample"></a>ReadMe pour l'exemple d'authentification de protection étendue

La protection étendue est une initiative de sécurité visant à se protéger contre les attaques de l’intercepteur (intercepteur), dans lesquelles un attaquant (le « Man-in-the-Middle ») intercepte les informations d’identification d’un client et les utilise pour accéder à des ressources sécurisées sur le serveur prévu du client.

Pour plus d’informations, consultez [protection étendue de l’authentification vue d’ensemble](extended-protection-for-authentication-overview.md).

> [!NOTE]
> Cet exemple fonctionne uniquement dans le cadre d'un hébergement sur IIS. Ile ne fonctionne pas sur Visual Studio Development Server car il ne prend pas en charge HTTPS.

## <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple

1. Installez IIS sur l’ordinateur à partir de Ajout/suppression de programmes-> fonctionnalités Windows.

2. Activer l’authentification Windows dans les fonctionnalités Windows : Internet Information Services-> World Wide Web services-> la sécurité > l’authentification Windows.

3. Activer l’activation HTTP dans les fonctionnalités Windows : Microsoft .NET Framework 3.5.1-> Windows Communication Foundation l’activation HTTP.

4. Cet exemple requiert l'établissement par le client d'un canal sécurisé avec le serveur et nécessite la présence d'un certificat de serveur qui peut être installé à partir du gestionnaire des services IIS (Internet Information Services).

    1. Ouvrez le gestionnaire des services Internet-> certificats de serveur (à partir de l’onglet Affichage des fonctionnalités).

    2. À des fins de test de cet exemple, vous pouvez créer un certificat auto-signé. (Si vous ne souhaitez pas qu'Internet Explorer vous informe que le certificat n'est pas sécurisé, vous pouvez l'installer dans la banque d'autorités racine approuvées de certificats).

5. Accédez au volet Actions pour le site web par défaut. Cliquez sur modifier les liaisons de > de site. Ajoutez HTTPS comme type s'il ne l'est pas encore, avec le numéro de port 443, et affectez le certificat SSL créé à l'étape précédente.

6. Générez le service. Un répertoire virtuel est alors créé dans IIS (à partir de l'action post-build spécifiée dans les propriétés de projet) et les fichiers dll, .svc et de configuration sont copiés comme requis pour l'hébergement d'un service sur le Web.

7. Ouvrez le gestionnaire des services IIS. Cliquez avec le bouton droit sur le répertoire virtuel (ExtendedProtection) que vous avez créé à l'étape précédente et sélectionnez Convertir en application.

8. Ouvrez le module Authentification dans le gestionnaire des services IIS de ce répertoire virtuel et activez l'authentification Windows.

9. Ouvrez les paramètres avancés de l'authentification Windows pour ce répertoire virtuel et définissez la valeur Requis, car, dans cet exemple, le paramètre ExtendedProtection correspondant est défini sur Toujours.

10. Vous pouvez tester le service en accédant à l'URL depuis une fenêtre de navigateur. Si vous souhaitez accéder à cette URL depuis plusieurs ordinateurs, assurez-vous que le pare-feu est ouvert pour l'ensemble des connexions HTTP et HTTPS entrantes.

11. Ouvrez le fichier de configuration client et fournissez un nom d’ordinateur complet pour l' \<client>  -  \<endpoint> attribut-address, en remplaçant \<full_machine_name> .

12. Exécutez le client. Le client communique avec le service en établissant un canal sécurisé et en utilisant une protection étendue de manière discrète.

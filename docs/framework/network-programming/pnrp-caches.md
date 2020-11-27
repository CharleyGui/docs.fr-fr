---
title: Caches PNRP
ms.date: 03/30/2017
ms.assetid: 270068d9-1b6b-4eb9-9e14-e02326bb88df
ms.openlocfilehash: 6f45b6d829867d830a9a10acf11e8456ba65d29e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263215"
---
# <a name="pnrp-caches"></a>Caches PNRP

Les caches PNRP sont des collections locales de points de terminaison sélectionnés par algorithme et conservés dans un pair.  
  
## <a name="pnrp-cache-initialization"></a>Initialisation du cache PNRP  

 Pour initialiser le cache PNRP ou la collection d’enregistrements de noms de pairs, au démarrage d’un nœud pair, utilisez l’une des méthodes suivantes :  
  
- Les entrées du cache permanent qui étaient présentes lorsque le nœud a été arrêté sont chargées à partir du disque dur de stockage.  
  
- Si une application utilise l’infrastructure de collaboration P2P, les informations de collaboration sont disponibles dans le gestionnaire de contacts de ce nœud.  
  
## <a name="scaling-peer-name-resolution-with-a-multi-level-cache"></a>Mise à l’échelle de la résolution de noms de pairs avec un cache à plusieurs niveaux  

 Pour minimiser la taille des caches PNRP, les nœuds pairs utilisent un cache à plusieurs niveaux, dans lequel chaque niveau contient un nombre maximal d’entrées. Chaque niveau du cache représente un dixième de l’espace de nombre des ID PNRP (2<sup>256</sup>). Le niveau le plus bas du cache contient un ID PNRP inscrit localement et d’autres ID PNRP qui sont numériquement proches de lui. Étant donné qu’un niveau de cache comprend un maximum de 20 entrées, un niveau inférieur est créé. Le nombre maximal de niveaux du cache est en base 10 (nombre total d’ID PNRP dans le cloud). Par exemple, pour un cloud global comprenant 100 millions d’ID PNRP, le cache comprend seulement 8 niveaux (=log10(100 000 000)) et un nombre similaire de tronçons pour résoudre un ID PNRP lors de la résolution de noms. Ce mécanisme permet l’utilisation d’une table de hachage distribuée pour laquelle un ID PNRP arbitraire peut être résolu en transférant des requêtes PNRP au pair le plus proche, jusqu’à ce que le pair avec l’adresse pair certifiée correspondante soit trouvé.  
  
 Pour vérifier que la résolution peut s’effectuer, chaque fois qu’un nœud ajoute une entrée au niveau le plus bas de son cache, il transmet une copie de l’entrée à tous les nœuds du dernier niveau du cache.  
  
 Les entrées du cache sont actualisées au fur et à mesure. Les entrées du cache qui sont périmées sont supprimées du cache. De cette façon, la table de hachage distribuée comprenant les ID PNRP est basée sur des points de terminaison actifs, contrairement au DNS dont les enregistrements d’adresses et le protocole ne fournissent aucune garantie que le nœud associé à l’adresse est actif sur le réseau.  
  
## <a name="other-pnrp-caches"></a>Autres caches PNRP  

 Le cache local est un autre exemple de magasin de données persistantes.  Outre les objets nécessaires à l’activité PNRP, il peut inclure des enregistrements associés à un cloud PNRP ou à une session de collaboration publiés de manière sécurisée et synchronisés entre tous les membres du cloud. Ce magasin répliqué représente la vue des données du groupe, qui doit être la même pour tous les membres du groupe. Techniquement, ces objets ne sont pas vraiment des enregistrements, mais plutôt des données d’application, de présence et d’objets destinées à un cache local. L’utilisation du cloud PNRP permet de garantir que les objets seront propagés vers tous les nœuds de la session de collaboration ou du cloud PNRP.  La réplication des enregistrements entre les membres du cloud utilise le protocole SSL pour le chiffrement et l’intégrité des données.  
  
 Lorsqu’un pair rejoint un cloud, il ne reçoit pas automatiquement les données du cache local de l’hôte pair auquel il est attaché. Il doit s’abonner à l’hôte pair pour recevoir les mises à jour des données d’application, de présence et d’objet. Après la première synchronisation, les pairs resynchronisent régulièrement leurs magasins répliqués pour garantir que tous les membres du groupe disposent de la même vue.  La session de collaboration ou les applications qu’elle contient peuvent servir la même fonction.  
  
 Après le démarrage d’une session de collaboration dans le cloud, les applications peuvent inscrire des pairs et commencer à publier leurs informations à l’aide de la stratégie de sécurité définie par l’étendue du cloud. Lorsqu’un pair rejoint un cloud, les mécanismes de sécurité du cloud sont appliqués au pair, et celui-ci se voit attribuer une étendue dans laquelle participer.  Ses enregistrements peuvent ensuite être publiés en toute sécurité dans l’étendue du cloud. Notez que l’étendue du cloud peut ne pas être la même que celle de l’application de collaboration.  
  
 Les pairs peuvent s’inscrire pour recevoir des objets provenant d’autres pairs. Lorsqu’un objet est mis à jour, l’application de collaboration en est informée et le nouvel objet est passé à tous les abonnés de l’application. Par exemple, un pair d’une application de discussion de groupe peut s’inscrire pour recevoir les informations de l’application. Il va alors recevoir tous les enregistrements de discussions sous forme de données d’application,  ce qui lui permettra de surveiller l’activité de discussion dans le cloud.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Net.PeerToPeer>

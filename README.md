# anvil-netboot

Démarrage réseau (iPXE, netboot OVH) du serveur Proxmox « anvil » via **ZFSBootMenu**, parce que GRUB ne sait
plus lire son pool ZFS racine.

- `anvil.ipxe` : script iPXE (deux sources : release GitHub, puis raw.githubusercontent).
- `zbm/` : `vmlinuz-bootmenu` + `initramfs-bootmenu.img` de **ZFSBootMenu v3.1.0** (build officiel
  `zfsbootmenu-release-x86_64-v3.1.0-linux6.12`, OpenZFS 2.4.0), **non modifiés** ; empreintes dans `zbm/SHA256SUMS`.
  Sources et licences (ZFSBootMenu : MIT ; noyau Linux : GPL-2.0 ; OpenZFS : CDDL) :
  https://github.com/zbm-dev/zfsbootmenu/releases/tag/v3.1.0

Chaque fichier est signé (`*.sig`, CMS détaché) par l'autorité `anvil-netboot-ca.crt` (certificat public ; la clé privée n'est pas ici) ; iPXE refuse tout fichier non signé.

Aucun secret ici : seul le hostid du serveur (non sensible) figure dans le script.

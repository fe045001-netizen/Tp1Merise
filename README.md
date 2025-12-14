# Lab 1 — Gestion de stock (Entrée) : Dictionnaire, Règles, MCD, MLD

# MCD :

![URL](https://github.com/fe045001-netizen/Tp1Merise/blob/8a5124bba0aa10db281d34b6b66471f40ad42bbd/mcd1.png)

# MPD:

![URL](https://github.com/fe045001-netizen/Tp1Merise/blob/8a5124bba0aa10db281d34b6b66471f40ad42bbd/MPD.png)

/*==============================================================*/
/* Nom de SGBD :  MySQL 4.0                                     */
/* Date de création :  14/12/2025 20:47:51                      */
/*==============================================================*/


drop index FOURNIR2_FK on FOURNIR;

drop index FOURNIR_FK on FOURNIR;

drop table if exists FOURNIR;

drop table if exists FOURNISSEUR;

drop table if exists PRODUIT;

/*==============================================================*/
/* Table : FOURNIR                                              */
/*==============================================================*/
create table FOURNIR
(
   CODEPROD                       longtext                       not null,
   NUMF                           int                            not null,
   PRIXACHAT                      decimal,
   primary key (CODEPROD, NUMF)
)
type = InnoDB;

/*==============================================================*/
/* Index : FOURNIR_FK                                           */
/*==============================================================*/
create index FOURNIR_FK on FOURNIR
(
   CODEPROD
);

/*==============================================================*/
/* Index : FOURNIR2_FK                                          */
/*==============================================================*/
create index FOURNIR2_FK on FOURNIR
(
   NUMF
);

/*==============================================================*/
/* Table : FOURNISSEUR                                          */
/*==============================================================*/
create table FOURNISSEUR
(
   NUMF                           int                            not null,
   NOMF                           longtext,
   ADRESSEF                       longtext,
   primary key (NUMF)
)
type = InnoDB;

/*==============================================================*/
/* Table : PRODUIT                                              */
/*==============================================================*/
create table PRODUIT
(
   CODEPROD                       longtext                       not null,
   DESIGPROD                      longtext,
   PRIXUNIT                       decimal,
   primary key (CODEPROD)
)
type = InnoDB;

alter table FOURNIR add constraint FK_FOURNIR foreign key (CODEPROD)
      references PRODUIT (CODEPROD) on delete restrict on update restrict;

alter table FOURNIR add constraint FK_FOURNIR2 foreign key (NUMF)
      references FOURNISSEUR (NUMF) on delete restrict on update restrict;

```

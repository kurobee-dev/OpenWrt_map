# OpenWrt_map
OpenWrtのmap.shをカスタマイズしたのでメモ

/etc/config/network のmap-e interfaceに下記のoptionを追加することでiptablesのSNATルールの総数を制限可能にした。
option snatpslimit='nn'

map-e interface にて割り当てられたportsetの内、任意のportをDNATする際にsnatpslimitによりSNATから除外されたportsetを利用可能にする。
map.sh内にてportsetは若いport no.のsetからfirewallに追加されていくため、除外されるportsetは先頭からnn個より後のportsetとなる。
option snatpslimit='nn' を指定しない時は4096がdefault値となり、割り当てられた全てのportsetがSNATされる。
default 4096 の根拠は、16port/set * 4096 = 65536 (port上限)である。


# OpenWrt_map
## OpenWrtのmap.shをカスタマイズしたのでメモ

/etc/config/network のmap-e interfaceに下記のoptionを追加することでiptablesのSNATルールを範囲指定可能とした。
	option snatstartps '32'  (default 1)
	option snatendps '62'  (default 4096)

map-e interface にて割り当てられたportsetの内、任意のportをDNATする為に指定範囲から除外されたportsetを利用可能にする。
optionを指定しない時（または存在しない時）はdefault値の範囲でSNATされる。
default 4096 の根拠は、16port/set * 4096 = 65536 (port上限)である。


# miniupnpd
patch zero interval upnpd for OpenWRT

# compile
git clone https://git.openwrt.org/openwrt/openwrt.git

cd openwrt


echo 'src-git upnpdfix https://github.com/mrFallon/miniupnpd.git' >> feeds.conf.default

./scripts/feeds update -a

./scripts/feeds install -a

rsync -a feeds/upnpdfix/net/ feeds/packages/net/


#make defconfig

make menuconfig

#select network-firewall-miniupnpd-nftables

make -j4

#make package/miniupnpd/{clean,prepare,compile} V=sc

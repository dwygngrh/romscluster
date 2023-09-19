## romscluster

Model2roms untuk buat forcing di ROMS rutgers, bukan di croco

## coba model2roms make grid croco

# buat 1 area kecil di roms croco. 

misal banda, resolusi 1/8

running matlab :

make grid

make_OGCM_mercator (download 2 bulan tahun 2022)

# running model2roms
Download CMEMS make script python

Setiap variabel akan di download ke setiap folder (thetao, so, uo,vo,zos)

python runM2R.py (cek konfigurasi di file configM2R.py)


# Error

perbedaan grid croco dan rustgers ada di informasi grid


# make_OGCM_mercator baru


if strcmp(OGCM,'mercator')
    if Ymin < 2020
        % ========================
        % For GLORYS 12 reanalysis extraction + download using python motuclient
        % ========================
        raw_mercator_name = 'mercator';
        kdata="DAILY" ; % or DAILY
        motu_url_reana='http://my.cmems-du.eu/motu-web/Motu';
        service_id_reana='GLOBAL_MULTIYEAR_PHY_001_030-TDS';
        if strcmp(kdata,"DAILY")
            product_id_reana='cmems_mod_glo_phy_my_0.083_P1D-m';
        elseif strcmp(kdata,"MONTHLY")
            product_id_reana='cmems_mod_glo_phy_my_0.083_P1M-m'
        else
            disp("Please specify what reanalysis frequency you want (DAILY or MONTHLY)")
        end
    else
        raw_mercator_name = 'mercator';
        kdata="DAILY" ; % or DAILY
        motu_url_reana='https://nrt.cmems-du.eu/motu-web/Motu';
        service_id_reana='GLOBAL_ANALYSISFORECAST_PHY_001_024-TDS';
%         if strcmp(kdata,"DAILY")
        product_id_reana='global-analysis-forecast-phy-001-024';
        product_id_cur='cmems_mod_glo_phy-cur_anfc_0.083deg_P1D-m'
        product_id_sal='cmems_mod_glo_phy-so_anfc_0.083deg_P1D-m';
        product_id_tem='cmems_mod_glo_phy-thetao_anfc_0.083deg_P1D-m';
        product_id_ssh='cmems_mod_glo_phy_anfc_0.083deg_P1D-m';
%         elseif strcmp(kdata,"MONTHLY")
%             product_id_reana='cmems_mod_glo_phy_my_0.083_P1M-m'
%         else
%             disp("Please specify what reanalysis frequency you want (DAILY or MONTHLY)")
    end
end

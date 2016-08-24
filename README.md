# Get-Mac-Address-Of-Android-Device

==> For Android Marshmallow Device Use following Code Snippet

    public static String getMacAddr(String str) {

        try {

            List<NetworkInterface> all = Collections.list(NetworkInterface.getNetworkInterfaces());

            for (NetworkInterface nif : all) {

                if (!nif.getName().equalsIgnoreCase("wlan0")) continue;

                byte[] macBytes = nif.getHardwareAddress();
                if (macBytes == null) {

                    return "";

                }

                StringBuilder res1 = new StringBuilder();
                for (byte b : macBytes) {

                    res1.append(Integer.toHexString(b & 0xFF) + ":");

                }

                if (res1.length() > 0) {

                    res1.deleteCharAt(res1.length() - 1);

                }

                return res1.toString();

            }
        } catch (Exception ex) {
        }

        return "02:00:00:00:00:00";

    }
    
==> For other android device use following code snippet

    WifiManager wifiManager = (WifiManager) getSystemService(Activity.WIFI_SERVICE);
    WifiInfo wInfo = wifiManager.getConnectionInfo();
    String macAddress = wInfo.getMacAddress();
    
    
    
Note : Use following link for above code...

                        http://robinhenniges.com/en/android6-get-mac-address-programmatically

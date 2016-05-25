# Generate key hash for android for Facebook integration

Put this code into your onCreate() method

              try {
                    PackageInfo info = getPackageManager().getPackageInfo(
                            getPackageName(),
                            PackageManager.GET_SIGNATURES);
                    for (android.content.pm.Signature signature : info.signatures) {
                        MessageDigest md = MessageDigest.getInstance("SHA");
                        md.update(signature.toByteArray());
                        Log.d("KeyHash:", Base64.encodeToString(md.digest(), Base64.DEFAULT));
                    }
                }
                catch (PackageManager.NameNotFoundException e) {

                }
                catch (NoSuchAlgorithmException e) {

                }

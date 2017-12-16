# Homework02
{
 "cells": [
  {
   "cell_type": "code",
   "execution_count": 3,
   "metadata": {
    "collapsed": true
   },
   "outputs": [],
   "source": [
    "# Dependencies\n",
    "import tweepy\n",
    "import json\n",
    "import pandas as pd\n",
    "import matplotlib.pyplot as plt\n",
    "\n",
    "# Twitter API Keys\n",
    "consumer_key = \"Ed4RNulN1lp7AbOooHa9STCoU\"\n",
    "consumer_secret = \"P7cUJlmJZq0VaCY0Jg7COliwQqzK0qYEyUF9Y0idx4ujb3ZlW5\"\n",
    "access_token = \"839621358724198402-dzdOsx2WWHrSuBwyNUiqSEnTivHozAZ\"\n",
    "access_token_secret = \"dCZ80uNRbFDjxdU2EckmNiSckdoATach6Q8zb7YYYE5ER\"\n",
    "\n",
    "\n",
    "# Setup Tweepy API Authentication\n",
    "auth = tweepy.OAuthHandler(consumer_key, consumer_secret)\n",
    "auth.set_access_token(access_token, access_token_secret)\n",
    "api = tweepy.API(auth, parser=tweepy.parsers.JSONParser())"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 4,
   "metadata": {
    "collapsed": false
   },
   "outputs": [
    {
     "ename": "FileNotFoundError",
     "evalue": "File b'PopularAcounts.csv' does not exist",
     "traceback": [
      "\u001b[0;31m---------------------------------------------------------------------------\u001b[0m",
      "\u001b[0;31mFileNotFoundError\u001b[0m                         Traceback (most recent call last)",
      "\u001b[0;32m<ipython-input-4-9976924b4b20>\u001b[0m in \u001b[0;36m<module>\u001b[0;34m()\u001b[0m\n\u001b[1;32m      1\u001b[0m \u001b[0;31m# Import CSV file into Data Frame\u001b[0m\u001b[0;34m\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[0;32m----> 2\u001b[0;31m \u001b[0mpopular_tweeters\u001b[0m \u001b[0;34m=\u001b[0m \u001b[0mpd\u001b[0m\u001b[0;34m.\u001b[0m\u001b[0mread_csv\u001b[0m\u001b[0;34m(\u001b[0m\u001b[0;34m\"PopularAcounts.csv\"\u001b[0m\u001b[0;34m,\u001b[0m \u001b[0mdtype\u001b[0m\u001b[0;34m=\u001b[0m\u001b[0mstr\u001b[0m\u001b[0;34m)\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[0m\u001b[1;32m      3\u001b[0m \u001b[0;34m\u001b[0m\u001b[0m\n\u001b[1;32m      4\u001b[0m \u001b[0;31m# Iterate through DataFrame\u001b[0m\u001b[0;34m\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[1;32m      5\u001b[0m \u001b[0;32mfor\u001b[0m \u001b[0mindex\u001b[0m\u001b[0;34m,\u001b[0m \u001b[0mrow\u001b[0m \u001b[0;32min\u001b[0m \u001b[0mpopular_tweeters\u001b[0m\u001b[0;34m.\u001b[0m\u001b[0miterrows\u001b[0m\u001b[0;34m(\u001b[0m\u001b[0;34m)\u001b[0m\u001b[0;34m:\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n",
      "\u001b[0;32m/Users/matthewgiordanella/anaconda/lib/python3.6/site-packages/pandas/io/parsers.py\u001b[0m in \u001b[0;36mparser_f\u001b[0;34m(filepath_or_buffer, sep, delimiter, header, names, index_col, usecols, squeeze, prefix, mangle_dupe_cols, dtype, engine, converters, true_values, false_values, skipinitialspace, skiprows, nrows, na_values, keep_default_na, na_filter, verbose, skip_blank_lines, parse_dates, infer_datetime_format, keep_date_col, date_parser, dayfirst, iterator, chunksize, compression, thousands, decimal, lineterminator, quotechar, quoting, escapechar, comment, encoding, dialect, tupleize_cols, error_bad_lines, warn_bad_lines, skipfooter, skip_footer, doublequote, delim_whitespace, as_recarray, compact_ints, use_unsigned, low_memory, buffer_lines, memory_map, float_precision)\u001b[0m\n\u001b[1;32m    644\u001b[0m                     skip_blank_lines=skip_blank_lines)\n\u001b[1;32m    645\u001b[0m \u001b[0;34m\u001b[0m\u001b[0m\n\u001b[0;32m--> 646\u001b[0;31m         \u001b[0;32mreturn\u001b[0m \u001b[0m_read\u001b[0m\u001b[0;34m(\u001b[0m\u001b[0mfilepath_or_buffer\u001b[0m\u001b[0;34m,\u001b[0m \u001b[0mkwds\u001b[0m\u001b[0;34m)\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[0m\u001b[1;32m    647\u001b[0m \u001b[0;34m\u001b[0m\u001b[0m\n\u001b[1;32m    648\u001b[0m     \u001b[0mparser_f\u001b[0m\u001b[0;34m.\u001b[0m\u001b[0m__name__\u001b[0m \u001b[0;34m=\u001b[0m \u001b[0mname\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n",
      "\u001b[0;32m/Users/matthewgiordanella/anaconda/lib/python3.6/site-packages/pandas/io/parsers.py\u001b[0m in \u001b[0;36m_read\u001b[0;34m(filepath_or_buffer, kwds)\u001b[0m\n\u001b[1;32m    387\u001b[0m \u001b[0;34m\u001b[0m\u001b[0m\n\u001b[1;32m    388\u001b[0m     \u001b[0;31m# Create the parser.\u001b[0m\u001b[0;34m\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[0;32m--> 389\u001b[0;31m     \u001b[0mparser\u001b[0m \u001b[0;34m=\u001b[0m \u001b[0mTextFileReader\u001b[0m\u001b[0;34m(\u001b[0m\u001b[0mfilepath_or_buffer\u001b[0m\u001b[0;34m,\u001b[0m \u001b[0;34m**\u001b[0m\u001b[0mkwds\u001b[0m\u001b[0;34m)\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[0m\u001b[1;32m    390\u001b[0m \u001b[0;34m\u001b[0m\u001b[0m\n\u001b[1;32m    391\u001b[0m     \u001b[0;32mif\u001b[0m \u001b[0;34m(\u001b[0m\u001b[0mnrows\u001b[0m \u001b[0;32mis\u001b[0m \u001b[0;32mnot\u001b[0m \u001b[0;32mNone\u001b[0m\u001b[0;34m)\u001b[0m \u001b[0;32mand\u001b[0m \u001b[0;34m(\u001b[0m\u001b[0mchunksize\u001b[0m \u001b[0;32mis\u001b[0m \u001b[0;32mnot\u001b[0m \u001b[0;32mNone\u001b[0m\u001b[0;34m)\u001b[0m\u001b[0;34m:\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n",
      "\u001b[0;32m/Users/matthewgiordanella/anaconda/lib/python3.6/site-packages/pandas/io/parsers.py\u001b[0m in \u001b[0;36m__init__\u001b[0;34m(self, f, engine, **kwds)\u001b[0m\n\u001b[1;32m    728\u001b[0m             \u001b[0mself\u001b[0m\u001b[0;34m.\u001b[0m\u001b[0moptions\u001b[0m\u001b[0;34m[\u001b[0m\u001b[0;34m'has_index_names'\u001b[0m\u001b[0;34m]\u001b[0m \u001b[0;34m=\u001b[0m \u001b[0mkwds\u001b[0m\u001b[0;34m[\u001b[0m\u001b[0;34m'has_index_names'\u001b[0m\u001b[0;34m]\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[1;32m    729\u001b[0m \u001b[0;34m\u001b[0m\u001b[0m\n\u001b[0;32m--> 730\u001b[0;31m         \u001b[0mself\u001b[0m\u001b[0;34m.\u001b[0m\u001b[0m_make_engine\u001b[0m\u001b[0;34m(\u001b[0m\u001b[0mself\u001b[0m\u001b[0;34m.\u001b[0m\u001b[0mengine\u001b[0m\u001b[0;34m)\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[0m\u001b[1;32m    731\u001b[0m \u001b[0;34m\u001b[0m\u001b[0m\n\u001b[1;32m    732\u001b[0m     \u001b[0;32mdef\u001b[0m \u001b[0mclose\u001b[0m\u001b[0;34m(\u001b[0m\u001b[0mself\u001b[0m\u001b[0;34m)\u001b[0m\u001b[0;34m:\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n",
      "\u001b[0;32m/Users/matthewgiordanella/anaconda/lib/python3.6/site-packages/pandas/io/parsers.py\u001b[0m in \u001b[0;36m_make_engine\u001b[0;34m(self, engine)\u001b[0m\n\u001b[1;32m    921\u001b[0m     \u001b[0;32mdef\u001b[0m \u001b[0m_make_engine\u001b[0m\u001b[0;34m(\u001b[0m\u001b[0mself\u001b[0m\u001b[0;34m,\u001b[0m \u001b[0mengine\u001b[0m\u001b[0;34m=\u001b[0m\u001b[0;34m'c'\u001b[0m\u001b[0;34m)\u001b[0m\u001b[0;34m:\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[1;32m    922\u001b[0m         \u001b[0;32mif\u001b[0m \u001b[0mengine\u001b[0m \u001b[0;34m==\u001b[0m \u001b[0;34m'c'\u001b[0m\u001b[0;34m:\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[0;32m--> 923\u001b[0;31m             \u001b[0mself\u001b[0m\u001b[0;34m.\u001b[0m\u001b[0m_engine\u001b[0m \u001b[0;34m=\u001b[0m \u001b[0mCParserWrapper\u001b[0m\u001b[0;34m(\u001b[0m\u001b[0mself\u001b[0m\u001b[0;34m.\u001b[0m\u001b[0mf\u001b[0m\u001b[0;34m,\u001b[0m \u001b[0;34m**\u001b[0m\u001b[0mself\u001b[0m\u001b[0;34m.\u001b[0m\u001b[0moptions\u001b[0m\u001b[0;34m)\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[0m\u001b[1;32m    924\u001b[0m         \u001b[0;32melse\u001b[0m\u001b[0;34m:\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[1;32m    925\u001b[0m             \u001b[0;32mif\u001b[0m \u001b[0mengine\u001b[0m \u001b[0;34m==\u001b[0m \u001b[0;34m'python'\u001b[0m\u001b[0;34m:\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n",
      "\u001b[0;32m/Users/matthewgiordanella/anaconda/lib/python3.6/site-packages/pandas/io/parsers.py\u001b[0m in \u001b[0;36m__init__\u001b[0;34m(self, src, **kwds)\u001b[0m\n\u001b[1;32m   1388\u001b[0m         \u001b[0mkwds\u001b[0m\u001b[0;34m[\u001b[0m\u001b[0;34m'allow_leading_cols'\u001b[0m\u001b[0;34m]\u001b[0m \u001b[0;34m=\u001b[0m \u001b[0mself\u001b[0m\u001b[0;34m.\u001b[0m\u001b[0mindex_col\u001b[0m \u001b[0;32mis\u001b[0m \u001b[0;32mnot\u001b[0m \u001b[0;32mFalse\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[1;32m   1389\u001b[0m \u001b[0;34m\u001b[0m\u001b[0m\n\u001b[0;32m-> 1390\u001b[0;31m         \u001b[0mself\u001b[0m\u001b[0;34m.\u001b[0m\u001b[0m_reader\u001b[0m \u001b[0;34m=\u001b[0m \u001b[0m_parser\u001b[0m\u001b[0;34m.\u001b[0m\u001b[0mTextReader\u001b[0m\u001b[0;34m(\u001b[0m\u001b[0msrc\u001b[0m\u001b[0;34m,\u001b[0m \u001b[0;34m**\u001b[0m\u001b[0mkwds\u001b[0m\u001b[0;34m)\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[0m\u001b[1;32m   1391\u001b[0m \u001b[0;34m\u001b[0m\u001b[0m\n\u001b[1;32m   1392\u001b[0m         \u001b[0;31m# XXX\u001b[0m\u001b[0;34m\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n",
      "\u001b[0;32mpandas/parser.pyx\u001b[0m in \u001b[0;36mpandas.parser.TextReader.__cinit__ (pandas/parser.c:4184)\u001b[0;34m()\u001b[0m\n",
      "\u001b[0;32mpandas/parser.pyx\u001b[0m in \u001b[0;36mpandas.parser.TextReader._setup_parser_source (pandas/parser.c:8449)\u001b[0;34m()\u001b[0m\n",
      "\u001b[0;31mFileNotFoundError\u001b[0m: File b'PopularAcounts.csv' does not exist"
     ],
     "output_type": "error"
    }
   ],
   "source": [
    "# Import CSV file into Data Frame\n",
    "popular_tweeters = pd.read_csv(\"PopularAcounts.csv\", dtype=str)\n",
    "\n",
    "# Iterate through DataFrame\n",
    "for index, row in popular_tweeters.iterrows():\n",
    "\n",
    "    # Grab the username\n",
    "    target_user = row[\"Screen Name\"]\n",
    "    # print(target_user)\n",
    "    \n",
    "    # Use the username with the Twitter API get_user\n",
    "    user_account = api.get_user(target_user)\n",
    "    user_real_name = user_account[\"name\"]\n",
    "    \n",
    "    # Get the specific column data\n",
    "    user_tweets = user_account[\"statuses_count\"]\n",
    "    user_followers = user_account[\"followers_count\"]\n",
    "    user_following = user_account[\"friends_count\"]\n",
    "    user_favorites = user_account[\"favourites_count\"]\n",
    "    \n",
    "    # Replace the row information for each\n",
    "    popular_tweeters.set_value(index, \"Real Name\", user_real_name)\n",
    "    popular_tweeters.set_value(index, \"Tweets\", user_tweets)\n",
    "    popular_tweeters.set_value(index, \"Followers\", user_followers)\n",
    "    popular_tweeters.set_value(index, \"Following\", user_following)\n",
    "    popular_tweeters.set_value(index, \"Favorites Count\", user_favorites)\n",
    "    \n",
    "# Export the new CSV\n",
    "popular_tweeters.to_csv(\"PopularAcounts_New.csv\", index=False)\n",
    "\n",
    "# View the DataFrame\n",
    "popular_tweeters.head()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 21,
   "metadata": {
    "collapsed": false
   },
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>Average Favorites Count</th>\n",
       "      <th>Average Follower Count</th>\n",
       "      <th>Average Following Count</th>\n",
       "      <th>Average Tweet Count</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",

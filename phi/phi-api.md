PHI Inscriptions API
====================

API access is over HTTP through epigraphy.packhum.org/api/. Only GET
requests are implemented. All data is sent as either JSON or XML.
Several API methods take optional parameters, either as a segment in
the path or as an HTTP query parameter.


1. Retrieving a particular inscription using a PHI id
-----------------------------------------------------

    GET /text/:phi_id.json  => returns JSON

    GET /text/:phi_id.xml  => returns XML

    GET /text/:phi_id  => returns plain text

For example, 

    curl -i -XGET http://epigraphy.packhum.org/api/text/1.json

returns:

    HTTP/1.1 200 OK
    Server: nginx/1.4.2
    Date: Mon, 16 Sep 2013 20:09:00 GMT
    Content-Type: application/json; charset=utf-8
    Content-Length: 1215
    Connection: keep-alive
    Set-Cookie: JSESSIONID=og23si294in71nonh7wwv0naa;Path=/
    Last-Modified: Fri, 13 Sep 2013 03:45:50 GMT
    Expires: Tue, 17 Sep 2013 20:09:00 GMT
    Cache-Control: max-age=86400, pre-check=86400
    X-Lift-Version: 2.5

		{
			"phi":"1",
			"ref":"IG I³ 1",
			"source":"IG I³",
			"regionName":"Attica (IG I-III) : Attica",
			"regionID":"88",
			"betacode":"~a\"0010\"b\"001\"c\"IG I(3)\"d\"Att\"n1z1\nἔδοχσεν το͂ι δέμοι· τ̣[ὸς ἐ Σ]αλαμ̣[ῖνι κλερόχ]ος\nοἰκε͂ν ἐᾶ Σαλαμῖνι [․․5․․]λεν [․․․7․․․ Ἀθέ]νε-\nσι τελε͂ν καὶ στρατ[εύεσθ]αι ⋮ τ̣[ὰ δ’ ἐ Σαλαμῖνι] μ-\nὲ μι[σθ]ο͂ν, ἐὰ μὲ οἰκ[․․․7․․․]ο[․ μισθόμενο․ ⋮ ἐ]ὰ-\n~z5\nν δὲ μισθο͂ι, ἀποτί[νεν τὸ μισθόμενον καὶ τὸ] μ̣-\nισθο͂ντα ℎεκάτε[ρον ․․․․․․․․19․․․․․․․․․]\nἐς δεμόσιο[ν ∶ ἐσπράτεν δὲ τὸν ἄ]-\nρχο[ν]τα, ἐὰν [δὲ μέ, εὐθ]ύ[νεσθαι ∶ τ]-\nὰ δὲ [ℎ]όπλα π[αρέχεσ]θ̣α[ι αὐτὸς ∶ τ]-\n~z10\nριά[κ]οντα ∶ δρ[αχμο͂ν ⋮] ℎο[πλισμένο]-\nν δὲ [τ]ὸν ἄρχοντ[α τὰ ℎόπλα κρίν]-\nεν ⋮ [ἐπ]ὶ τε͂ς β[ο]λε͂[ς ․․․c.11․․․․]"
		}

2. Retrieving PHI ids by location
---------------------------------

		GET /refs.json?loc=:locid  => returns JSON

		GET /refs.xml?loc=:locid  => returns XML

The response is a map of PHI ids to conventional reference. Location 1
(:loc_id = 1) is the root location and will return a map of all PHI
ids.

For example,

	curl -i -XGET http://epigraphy.packhum.org/api/refs.json?loc=100

returns

		HTTP/1.1 200 OK
		Server: nginx/1.4.2
		Date: Mon, 16 Sep 2013 20:24:27 GMT
		Content-Type: application/json; charset=utf-8
		Content-Length: 838
		Connection: keep-alive
		Set-Cookie: JSESSIONID=pdtrmaf0y8gykcfbs30u7yfc;Path=/
		Last-Modified: Fri, 13 Sep 2013 03:45:50 GMT
		Expires: Tue, 17 Sep 2013 20:24:27 GMT
		Cache-Control: max-age=86400, pre-check=86400
		X-Lift-Version: 2.5

		[["143365","IG XIV 2545"],["143367","IG XIV 2547"],["143368","IG XIV 2548"],["143369","IG XIV 2549"],["143370","IG XIV 2550"],["143371","IG XIV 2551"],["143372","IG XIV 2552"],["143373","IG XIV 2553"],["143374","IG XIV 2554"],["143375","IG XIV 2555"],["143402","IG XIV 2573,2"],["143405","IG XIV 2573,5"],["143407","IG XIV 2573,7"],["143408","IG XIV 2573,8"],["143411","IG XIV 2573,11"],["143437","IG XIV 2576,4"],["143450","IG XIV 2577,6"],["143456","IG XIV 2577,12"],["330034","SEG 19:643"],["330035","SEG 19:644"],["330036","SEG 19:646"],["333742","SEG 30:1241"],["331327","SEG 34:1040"],["331790","SEG 37:840"],["332049","SEG 39:1089"],["332050","SEG 39:1090"],["332683","SEG 42:980"],["332684","SEG 42:981"],["340237","SEG 47:1543"],["336458","SEG 48:1310"],["336663","SEG 50:1086"],["337348","SEG 52:1018"],["337489","SEG 54:1011"]]

3. Retrieving PHI ids by source
-------------------------------

		GET /refs.json?source=:source_id  => returns JSON

		GET /refs.xml?source=:source_id  => returns XML

For example,

		curl -i -XGET http://epigraphy.packhum.org/api/refs.xml?source=295

returns

		HTTP/1.1 200 OK
		Server: nginx/1.4.2
		Date: Mon, 16 Sep 2013 20:41:47 GMT
		Content-Type: text/xml; charset=utf-8
		Content-Length: 1019
		Connection: keep-alive
		Set-Cookie: JSESSIONID=19f44uezh533y1m6sx0xhw0xl4;Path=/
		Last-Modified: Fri, 13 Sep 2013 03:45:50 GMT
		Expires: Tue, 17 Sep 2013 20:41:47 GMT
		Cache-Control: max-age=86400, pre-check=86400
		X-Lift-Version: 2.5


		<?xml version="1.0" encoding="UTF-8"?>
		<refs><ref phi="201434">KretChr 1951:446</ref><ref phi="201435">KretChr 1952:479</ref><ref phi="201436">KretChr 1953:358,1</ref><ref phi="201437">KretChr 1953:358,2</ref><ref phi="201438">KretChr 1954:515</ref><ref phi="201439">KretChr 1955:567</ref><ref phi="201440">KretChr 1956:419</ref><ref phi="201441">KretChr 1956:420</ref><ref phi="201442">KretChr 1957:339(1)</ref><ref phi="201443">KretChr 1957:339(2)</ref><ref phi="201444">KretChr 1958:482</ref><ref phi="201445">KretChr 1959:392</ref><ref phi="201446">KretChr 1969:28/32</ref><ref phi="201447">KretChr 1969:281,2</ref><ref phi="201448">KretChr 1969:318,8</ref><ref phi="201449">KretChr 1969:319,9</ref><ref phi="201450">KretChr 1969:320,12</ref><ref phi="201451">KretChr 1969:322,16</ref><ref phi="201452">KretChr 1969:323,17a(1)</ref><ref phi="201453">KretChr 1969:323,17a(2)</ref><ref phi="201454">KretChr 1969:323,17c</ref><ref phi="201455">KretChr 1969:332</ref><ref phi="201456">KretChr 1970:518</ref></refs>  

4. Retrieving PHI locations
---------------------------

		GET /loc/:loc_id.json  => returns JSON

		GET /loc/:loc_id.xml   => returns XML

The locations are arranged hierarchically. The response represents a
graph of a location and its children. Location 1 is the root location.

For example,

		curl -i -XGET http://epigraphy.packhum.org/api/loc/10.json 

returns

		HTTP/1.1 200 OK
		Server: nginx/1.4.2
		Date: Mon, 16 Sep 2013 20:50:06 GMT
		Content-Type: application/json; charset=utf-8
		Content-Length: 188
		Connection: keep-alive
		Last-Modified: Fri, 13 Sep 2013 03:45:50 GMT
		Expires: Tue, 17 Sep 2013 20:49:10 GMT
		Cache-Control: max-age=86400, pre-check=86400
		X-Lift-Version: 2.5


		[10,"North Africa",[[92,"Mauretania Tingitana"],[93,"Mauretania Caesariensis"],[94,"Mauretania Sitifensis"],[95,"Numidia"],[96,"Tripolitania"],[97,"Byzacena"],[98,"Africa Proconsularis"]]]

5. Retrieving PHI sources
-------------------------

		GET /source.json  => returns JSON

		GET /source.xml   => returns XML

		GET /source.json?q=:search_pattern  => returns JSON

		GET /source.xml?q=:search_pattern   => returns XML

The first two calls return a complete list of sources. The second two
interpret :search_pattern as a regular expression and use it to filter
sources by title.

For example, 

		curl -i -XGET http://epigraphy.packhum.org/api/source.json?q="Aphrod"

returns

		HTTP/1.1 200 OK
		Server: nginx/1.4.2
		Date: Mon, 16 Sep 2013 21:13:22 GMT
		Content-Type: application/json; charset=utf-8
		Content-Length: 91
		Connection: keep-alive
		Set-Cookie: JSESSIONID=1bd9yp7t4yp2a19nix4pfrhe9a;Path=/
		Last-Modified: Fri, 13 Sep 2013 03:45:50 GMT
		Expires: Tue, 17 Sep 2013 21:13:22 GMT
		Cache-Control: max-age=86400, pre-check=86400
		X-Lift-Version: 2.5

		[["484","McCabe, Aphrodisias"],["532","Roueché, Performers and Partisans at Aphrodisias"]]
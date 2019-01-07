============
Atlantis DSL
============

Simple field based aggregations
*******************************

Scenario: KPI Metric (i.e. Average NO2 sofar for all sensors):: 

    {
    "aggs": {
        "1": {
        "avg": {
            "field": "metric_value"
        }
        }
    },
    "size": 0,
    "_source": {
        "excludes": []
    },
    "stored_fields": [
        "*"
    ],
    "script_fields": {},
    "docvalue_fields": [
        {
        "field": "timestamp",
        "format": "date_time"
        }
    ],
    "query": {
        "bool": {
        "must": [
            {
            "bool": {
                "should": [
                {
                    "match_phrase": {
                    "metric": "AQI"
                    }
                }
                ],
                "minimum_should_match": 1
            }
            }
        ],
        "filter": [
            {
            "match_all": {}
            }
        ],
        "should": [],
        "must_not": []
        }
    }
    }

 
Timeseries based aggregations
*******************************

Scenario: Daily Average of Multiple Metrics sofar::

    GET /metrics/_search?filter_path=aggregations
        {
            "aggs": {
                "intervalaggregation": {
                "date_histogram": {
                "field": "timestamp",
                "interval": "1d",
                "time_zone": "Asia/Kolkata",
                "format": "yyyy-MM-dd",
                "min_doc_count": 1
                },
            "aggs": {
                "metricgroup": {
                    "filter": {
                        "terms": {
                            "metric": [
                                "NO2",
                                "CO2",
                                "AQI"
                                ]
                         }
                 },
                "aggs": {
                    "metrics_by_day": {
                    "terms": {
                        "field": "metric",
                        "size": 100,
                        "order": {
                        "averagemetricvalue": "asc"
                        }
                    },
                    "aggs": {
                        "averagemetricvalue": {
                        "avg": {
                            "field": "metric_value"
                        }
                        }
                    }
                    }
                }
                }
            }
            }
        },
        "size": 0,
        "_source": {
            "excludes": []
        },
        "stored_fields": [
            "*"
        ],
        "script_fields": {},
        "docvalue_fields": [
            {
            "field": "timestamp",
            "format": "date_time"
            }
        ],
        "query": {
            "bool": {
            "must": [],
            "filter": [
                {
                "match_all": {}
                }
            ],
            "should": [],
            "must_not": []
            }
        }
        }

Scenario 3: XXXXX

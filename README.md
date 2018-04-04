# gengos
元号を2月以降に発表するという狂った日程になったので、政府元号を放棄して民間で新元号をとっとと決める

# サンプル
    const gengos = require('gengos')

    const dateToGengo = date => {
      let latestGengo = gengos[0]
      if(date.getTime() < latestGengo.start.getTime()){
        return undefined
      }
      for(let g of gengos){
        if(date.getTime() >= g.start.getTime()){
          latestGengo = g
        } else {
          return latestGengo
        }
      }
      return latestGengo
    }

    console.log('now ->', dateToGengo(new Date()))
    console.log('1970 ->', dateToGengo(new Date(1970,1)))
    console.log('1920 ->', dateToGengo(new Date(1920,1)))
    console.log('1900 ->', dateToGengo(new Date(1900,1)))
    console.log('1800 ->', dateToGengo(new Date(1800,1)))

表示
    now -> { name: '平成', start: 1989-02-07T15:00:00.000Z }
    1970 -> { name: '昭和', start: 1927-01-24T15:00:00.000Z }
    1920 -> { name: '大正', start: 1912-08-29T15:00:00.000Z }
    1900 -> { name: '明治', start: 1868-02-24T15:00:00.000Z }
    1800 -> undefined

# 私新元号の提案
issueへどうぞ
